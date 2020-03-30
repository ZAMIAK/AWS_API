<style scoped>
.video{
  width: 100%;
}
.wrapper{
  margin: 0 auto;
  width: 1000px;
}
</style>
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
            <v-list-item-title>Acceuil</v-list-item-title>
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
      <v-toolbar-title>Video player</v-toolbar-title>
    </v-app-bar>

    <v-content class="wrapper">
      <video src="./assets/golimar.mp4" controls class="video"></video>
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
            videoLink: null,
            drawer: false
        }
    },
    methods:{
      async getVideo(){
        let response = await this.$http.get("https://czrnafchb7.execute-api.eu-west-3.amazonaws.com/mrcfa/")
        this.videoLink = JSON.parse(response.data.body)
      }
    },
    mounted(){
        this.getVideo()
    }
}
</script>
<style scoped>

</style>