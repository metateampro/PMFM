<template>
    <v-content>
        <v-container
            fluid
            fill-height
        >
            <v-layout
            align-center
            justify-center
            >
            <v-tooltip right>
                <template v-slot:activator="{ on }">
                <v-btn
                    :href="source"
                    icon
                    large
                    target="_blank"
                    v-on="on"
                >
                    <v-icon large>mdi-code-tags</v-icon>
                </v-btn>
                </template>
                <span>Source</span>
            </v-tooltip>
            <v-tooltip right>
                <template v-slot:activator="{ on }">
                <v-btn
                    icon
                    large
                    href="https://codepen.io/johnjleider/pen/MNYLdL"
                    target="_blank"
                    v-on="on"
                >
                    <v-icon large>mdi-codepen</v-icon>
                </v-btn>
                </template>
                <span>Codepen</span>
            </v-tooltip>
        </v-layout>
        </v-container>
    </v-content>
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