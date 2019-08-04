<template>  
    <v-app-bar
    :clipped-left="$vuetify.breakpoint.lgAndUp"
    app
    color="blue darken-3"
    dark
    >
    <v-toolbar-title
        style="width: 300px"
        class="ml-0 pl-4"
    >
        <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
        <span class="hidden-sm-and-down">Google Contacts</span>
    </v-toolbar-title>
    <v-text-field
        flat
        solo-inverted
        hide-details
        prepend-inner-icon="mdi-search"
        label="Search"
        class="hidden-sm-and-down"
    ></v-text-field>
    <v-spacer></v-spacer>
    <v-btn icon>
        <v-icon>apps</v-icon>
    </v-btn>
    <v-btn icon>
        <v-icon>notifications</v-icon>
    </v-btn>
    <v-btn
        icon
        large
    >
        <v-avatar
        size="32px"
        item
        >
        <v-img
            src="https://cdn.vuetifyjs.com/images/logos/logo.svg"
            alt="Vuetify"
        >
        </v-img></v-avatar>
    </v-btn>
    </v-app-bar>
</template>

<script>
  export default {
    props: {
      source: String,
    },
    data: () => ({
      dialog: false,
      drawer: null,
      items: [
        { icon: 'mdi-contacts', text: 'Contacts' },
        { icon: 'mdi-history', text: 'Frequently contacted' },
        { icon: 'mdi-content_copy', text: 'Duplicates' },
        {
          icon: 'chevron-down',
          'icon-alt': 'chevron-down',
          text: 'Labels',
          model: true,
          children: [
            { icon: 'plus', text: 'Create label' },
          ],
        },
        {                                                                                                                                                                                 
          icon: 'mdi-chevron-down',
          'icon-alt': 'mdi-chevron-down',
          text: 'More',
          model: false,
          children: [
            { text: 'Import' },
            { text: 'Export' },
            { text: 'Print' },
            { text: 'Undo changes' },
            { text: 'Other contacts' },
          ],
        },
        { icon: 'mdi-settings-outline', text: 'Settings' },
        { icon: 'mdi-chat_bubble', text: 'Send feedback' },
        { icon: 'mdi-help', text: 'Help' },
        { icon: 'mdi-phonelink', text: 'App downloads' },
        { icon: 'mdi-keyboard', text: 'Go to the old version' },
      ],
    }),
  }
</script>