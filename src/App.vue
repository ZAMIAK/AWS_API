<template>
  <v-app id="inspire">
    <v-navigation-drawer
      v-model="drawer"
      app
    >
      <v-list dense>
        <v-list-item link>
          <v-list-item-action>
            <v-icon>mdi-home</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Home</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item link>
          <v-list-item-action>
            <v-icon>mdi-contact-mail</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Contact</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      app
      color="indigo"
      dark
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title>Application</v-toolbar-title>
    </v-app-bar>

    <v-content>
      <v-card
    max-width="600"
    class="mx-auto"
  >
    <v-toolbar
      color="light-blue"
      dark
    >
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>My files</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-view-module</v-icon>
      </v-btn>
    </v-toolbar>

    <v-list subheader>
      <v-subheader inset>Files</v-subheader>

      <v-list-item
        v-for="item in nomFichier"
        :key="item.id"
      >
        <v-list-item-avatar>
           <v-icon color="blue darken-2">mdi-message-text</v-icon>
        </v-list-item-avatar>

        <v-list-item-content>
          <v-list-item-title v-text="item"></v-list-item-title>
          <!-- <v-list-item-subtitle v-text="item.subtitle"></v-list-item-subtitle> -->
        </v-list-item-content>

        <!-- <v-list-item-action>
          <v-btn icon>
            <v-icon color="grey lighten-1">mdi-information</v-icon>
          </v-btn>
        </v-list-item-action> -->
      </v-list-item>
    </v-list>
  </v-card>
    </v-content>
    <v-footer
      color="indigo"
      app
    >
      <span class="white--text">&copy; 2020</span>
    </v-footer>
  </v-app>
</template>
<script>
export default {
    name: 'todos',
    props: {
      source: String,
    },
    data(){
        return{
            nomFichier: null,
            drawer: null
        }
    },
    methods:{
      async getAllfiles(){
        let response = await this.$http.get("https://czrnafchb7.execute-api.eu-west-3.amazonaws.com/mrcfa/")
        this.nomFichier = JSON.parse(response.data.body)
      }
    },
    mounted(){
        this.getAllfiles()
    }
}
</script>
<style scoped>

</style>