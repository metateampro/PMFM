<template>
    <v-navigation-drawer
      v-model="drawer"
      :clipped="$vuetify.breakpoint.lgAndUp"
      app>
      <v-list dense>
        <template v-for="item in items">
          <v-layout
            v-if="item.heading"
            :key="item.heading"
            align-center>
            <v-flex xs6>
              <v-subheader v-if="item.heading">
                {{ item.heading }}
              </v-subheader>
            </v-flex>
            <v-flex
              xs6
              class="text-center">
              <a href="#!" class="body-2 black--text">EDIT</a>
            </v-flex>
          </v-layout>
          <v-list-group
            v-else-if="item.children"
            :key="item.text"
            v-model="item.model"
            :prepend-icon="item.model ? item.icon : item['icon-alt']"
            append-icon="">
            <template v-slot:activator>
              <v-list-item>
                <v-list-item-content>
                  <v-list-item-title>
                    {{ item.text }}
                  </v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </template>
            <v-list-item
              v-for="(child, i) in item.children"
              :key="i"
              >
              <v-list-item-action v-if="child.icon">
                <v-icon>{{ child.icon }}</v-icon>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title>
                  {{ child.text }}
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list-group>
          <v-list-item
            v-else
            :key="item.text"
            :to="item.routerLink || '*'">
              <v-list-item-action>
                <v-icon>{{ item.icon }}</v-icon>
              </v-list-item-action>
              <v-list-item-content >
                <v-list-item-title>
                  {{ item.text }}
                </v-list-item-title>
              </v-list-item-content>
          </v-list-item>
        </template>
      </v-list>
    </v-navigation-drawer>
</template>

<script>
import AppBar from './AppBar.vue'
  export default {
    props: {
      source: String,
    },
    components:{
            'side-bar': AppBar
    },
    computed:{
        showSideBar(){
            this.$store.getters.g_sideBarOpen;
        }
    },
    data: () => ({
      dialog: false,
      drawer: null,
      items: [
        { icon: 'mdi-view-comfy', text: 'Информационная панель', routerLink: '/'},
        {
          icon: 'mdi-chevron-up', 'icon-alt': 'mdi-chevron-down',
          text: 'Реестры',
          model: true,
          children: [
            { text: 'Портфели' },
            { text: 'Комплексные проекты' },
            { text: 'Проекты' },
            { text: 'Контракты' },
          ],
        },
        { icon: 'mdi-clock-outline', text: 'Совещания' },
        { icon: 'mdi-calendar-star', text: 'Поручения' },
        { icon: 'mdi-message-reply-text', text: 'Открытые вопросы' },
        { icon: 'mdi-help', text: 'Техподдержка', routerLink: '/about' },
      ],
    }),
  }
</script>