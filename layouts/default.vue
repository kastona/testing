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

     


      <v-toolbar-title @click="$router.push('/')">
      <v-img
          :src="require('@/assets/logo2.png')"
          contain
         style="width: 200px"


        />
      </v-toolbar-title>


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
        :to="'/about'"
        class="ml-0 hidden-sm-and-down"
        text
      >
       About
      </v-btn>

      <v-btn
        v-if="$auth.user"
        nuxt
        :to="'/admin'"
        class="ml-0 hidden-sm-and-down"
        text
        color="black"
      >
       Admin
      </v-btn>
      

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
