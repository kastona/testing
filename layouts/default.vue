<template>
<div id="app" >
  <v-app style="background-color: #f1f1ff;" light>
    <v-app-bar
      color="primary"
      fixed
      dark
      app
      elevate-on-scroll
    >
      <v-app-bar-nav-icon class="hidden-md-and-up" @click="drawer = true"></v-app-bar-nav-icon>

      <v-avatar
        size="40"
        @click="$router.push('/')"
        color="grey lighten-5"
      >
        <v-img
          :src="require('@/assets/logo.png')"
          contain
          height="100%"


        />
      </v-avatar>


      <v-toolbar-title @click="$router.push('/')">Fob News</v-toolbar-title>


      <v-spacer></v-spacer>

      <v-btn
        nuxt
        :to="'/'"
        class="ml-0 hidden-sm-and-down"
        text
      >
        Home
      </v-btn>

      <v-btn
        nuxt
        :to="'/songs/audios'"
        class="ml-0 hidden-sm-and-down"
        text
      >
        Top Audio
      </v-btn>

      <v-btn
        nuxt
        :to="'/songs/videos'"
        class="ml-0 hidden-sm-and-down"
        text
      >
        Top Videos
      </v-btn>

      <v-btn
        nuxt
        :to="'/songs/new-releases'"
        class="ml-0 hidden-sm-and-down"
        text
      >
        New Releases
      </v-btn>


      <v-btn
        
        nuxt
        :to="'/admin'"
        class="ml-0 hidden-sm-and-down"
        text
        color="accent"
      >
       Admin
      </v-btn>
      
      
      <v-btn
        
        nuxt
        :to="'/login'"
        class="ml-0"
        text
      >
        Login
      </v-btn>

    </v-app-bar>

    <v-navigation-drawer
      v-model="drawer"
      fixed
      clipped
      app
    >
      <v-list
        nav
        dense
      >
        <v-list-item-group
          active-class="primary--text text--accent-4"
        >
          <v-list-item nuxt :to="'/'">
            <v-list-item-icon>
              <v-icon>mdi-home</v-icon>
            </v-list-item-icon>
            <v-list-item-title>Home</v-list-item-title>
          </v-list-item>


          <v-list-item nuxt :to="'/songs/audios'">
            <v-list-item-icon>
              <v-icon>mdi-music</v-icon>
            </v-list-item-icon>
            <v-list-item-title>Politics</v-list-item-title>
          </v-list-item>


          <v-list-item nuxt :to="'/songs/videos'">
            <v-list-item-icon>
              <v-icon>mdi-music</v-icon>
            </v-list-item-icon>
            <v-list-item-title>Crime</v-list-item-title>
          </v-list-item>

          <v-list-item nuxt :to="'/songs/new-releases'">
            <v-list-item-icon>
              <v-icon>mdi-music</v-icon>
            </v-list-item-icon>
            <v-list-item-title>Interviews</v-list-item-title>
          </v-list-item>

          <v-list-item nuxt :to="'/songs/new-releases'">
            <v-list-item-icon>
              <v-icon>mdi-music</v-icon>
            </v-list-item-icon>
            <v-list-item-title>About</v-list-item-title>
          </v-list-item>

          <v-list-item  nuxt :to="'/admin'">
            <v-list-item-icon>
              <v-icon>mdi-account-cog</v-icon>
            </v-list-item-icon>
            <v-list-item-title>Admin</v-list-item-title>
          </v-list-item>


        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>


    <v-main>
      <nuxt/>
    </v-main>
    <Footer/>
  </v-app>
</div>
</template>


<script>
  import Footer from '~/components/Footer'
  import {mapGetters} from 'vuex'
  export default {
    components: {
      Footer
    },

    data: () => ({
      drawer: false,
    }),

    methods: {
      onScroll (e) {
        this.showTopSearch = e.target.scrollTop
      },
    },

    computed: {
      ...mapGetters({
        
      }),
      
    }

  }
</script>
