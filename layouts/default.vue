<template>
<div id="app" >
  <v-app  light>
    <v-app-bar
      color="secondary"
      dark
      app
      elevate-on-scroll
    >
      <v-app-bar-nav-icon class="hidden-md-and-up" @click="draw = true"></v-app-bar-nav-icon>

     


      <v-avatar
        size="40"
        @click="$router.push('/')"
        color="grey lighten-5"
      >
        <v-img
          :src="require('@/assets/fob.png')"
          contain
          height="100%"


        />
      </v-avatar>


      <v-toolbar-title @click="$router.push('/')">FOB NEWS</v-toolbar-title>


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
        :to="'/news/politics'"
        class="ml-0 hidden-sm-and-down"
        text
      >
        Politics
      </v-btn>

      <v-btn
        nuxt
        :to="'/news/crime'"
        class="ml-0 hidden-sm-and-down"
        text
      >
        Crime
      </v-btn>

      <v-btn
        nuxt
        :to="'/interviews'"
        class="ml-0 hidden-sm-and-down"
        text
      >
       Interviews
      </v-btn>

       <v-btn
        nuxt
        :to="'/videos'"
        class="ml-0 hidden-sm-and-down"
        text
      >
       Videos
      </v-btn>

 <v-btn
        nuxt
        :to="'/entertainment'"
        class="ml-0 hidden-sm-and-down"
        text
      >
       Entertainment
      </v-btn>


<v-btn
        nuxt
        :to="'/education'"
        class="ml-0 hidden-sm-and-down"
        text
      >
       Education
      </v-btn>

      <v-btn
        nuxt
        :to="'/about'"
        class="ml-0 hidden-sm-and-down"
        text
      >
       About
      </v-btn>
      
<v-menu class="ml-0 hidden-sm-and-down" offset-y>
        <template v-slot:activator="{ on }">


          <v-btn icon v-on="on">
            <v-icon>mdi-dots-vertical</v-icon>
          </v-btn>
        </template>

        <v-list dense>
          <v-list-item nuxt-link to="/news/health">
            <v-list-item-title>Health</v-list-item-title>
          </v-list-item>

          <v-list-item nuxt-link to="/news/agriculture">
            <v-list-item-title>Agriculture</v-list-item-title>
          </v-list-item>

          <v-list-item nuxt-link to="/news/foreign">
            <v-list-item-title>Foreign</v-list-item-title>
          </v-list-item>

          <v-list-item nuxt-link to="/news/local">
            <v-list-item-title>Local</v-list-item-title>
          </v-list-item>

          <v-list-item nuxt-link to="/admin">
            <v-icon class="mr-2" color="primary">mdi-account</v-icon>
            <v-list-item-title>Admin</v-list-item-title>
          </v-list-item>


          <v-list-item @click="$auth.logout('local')">
            <v-icon class="mr-2" color="primary">mdi-logout</v-icon>
            <v-list-item-title>Log out</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>


      

    </v-app-bar>

    <v-navigation-drawer
      v-model="draw"
      fixed
      bottom
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


          <v-list-item nuxt :to="'/news/politics'">
            <v-list-item-title>Politics</v-list-item-title>
          </v-list-item>


          <v-list-item nuxt :to="'/news/crime'">
            <v-list-item-title>Crime</v-list-item-title>
          </v-list-item>

          <v-list-item nuxt :to="'/interviews'">
            
            <v-list-item-title>Interviews</v-list-item-title>
          </v-list-item>

          <v-list-item nuxt :to="'/news/entertainment'">
            <v-list-item-title>Entertainment</v-list-item-title>
          </v-list-item>

          <v-list-item nuxt :to="'/news/health'">
            <v-list-item-title>Health</v-list-item-title>
          </v-list-item>
          <v-list-item nuxt :to="'/news/agriculture'">
            <v-list-item-title>Agriculture</v-list-item-title>
          </v-list-item>

          <v-list-item nuxt :to="'/news/foreign'">
            <v-list-item-title>Foreign</v-list-item-title>
          </v-list-item>

          <v-list-item nuxt :to="'/news/local'">
            <v-list-item-title>Local</v-list-item-title>
          </v-list-item>

          <v-list-item nuxt :to="'/news/education'">
            <v-list-item-title>Education</v-list-item-title>
          </v-list-item>

          <v-list-item nuxt :to="'/about'">
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
    <Footer class="my-10"/>
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
      draw: false,
    }),

    methods: {
      
    },

    computed: {
      ...mapGetters({
        
      }),
      
    }

  }
</script>
