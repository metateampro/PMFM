<template>
  <v-app>
      <LeftBarMenu />

      <AppBar />


    <!-- Sizes your content based upon application components -->
    <v-content
       fluid
       fill-height>

      <!-- Provides the application the proper gutter -->
      <v-container fluid>

        <!-- If using vue-router -->
        <router-view></router-view>
      </v-container>
    </v-content>

    <v-footer app>
      <!-- -->
    </v-footer>
  </v-app>
</template>

<script lang="ts">
import Vue from 'vue';
import LeftBarMenu from './components/LeftBarMenu.vue';
import Authorization from './components/Authorization.vue';
import AppBar from './components/AppBar.vue';


export default Vue.extend({
  name: 'App',
  components: {
    LeftBarMenu,
    Authorization,
    AppBar,
  },
  data: () => ({
    //
  }),
});
</script>
