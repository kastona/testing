<template>
  <div>
    <section class="welcome-background">

      <v-container style="min-height: 65vh;" fluid fill-height>
        <v-layout flex align-center justify-center>
          <v-flex class="white--text text-center" xs12 md8 sm6>
              <h2 class=" display-2 font-weight-bold mb-3">
                FOB NEWS</h2>

              <v-responsive
                 class="mx-auto title font-weight-light mb-8"
                max-width="720"
              >
                Get involved
              </v-responsive>

          </v-flex>
        </v-layout>
      </v-container>
    </section>

    <section id="featured">
      <div class="py-12"></div>

      <v-container light class="text-center">
        <h2
            class="primary--text text--lighten-1 font-weight-bold mb-3">Headlines</h2 >

        <v-responsive
          class="mx-auto"
          width="56"
        >
          <v-divider v-if="!$vuetify.breakpoint.smAndDown" class="mb-1"></v-divider>

        </v-responsive>

        <v-row>
          <v-col
            v-for="n in 10"
            :key="n"
            cols="12"
            md="4"
            sm="6"
          >
            <v-card
    class="mx-auto"
    max-width="400"
  >
    <v-img
      class="white--text align-end"
      height="200px"
      src="https://cdn.vuetifyjs.com/images/cards/docks.jpg"
    >
      <v-card-title>Top 10 Australian beaches</v-card-title>
    </v-img>

    <v-card-subtitle class="pb-0">
      Number 10
    </v-card-subtitle>

    <v-card-text class="text--primary">
      <div>Whitehaven Beach</div>

      <div>Whitsunday Island, Whitsunday Islands</div>
    </v-card-text>

    <v-card-actions>
      <v-btn
        color="orange"
        text
      >
        Share
      </v-btn>

      <v-btn
        color="orange"
        text
      >
        Explore
      </v-btn>
    </v-card-actions>
  </v-card>
          </v-col>
        </v-row>

      </v-container>
    </section>
    <section style="background-color: #ebebeb;" id="about-us">
      <div class="py-5"></div>

      <v-container light class="text-center">
        <h2 :class="$vuetify.breakpoint.smAndDown?'h4': 'display-2'"
            class=" grey--text text--darken-1 font-weight-bold mb-3">About Benedictionz</h2>

        <v-responsive
          class="mx-auto mb-8"
          width="56"
        >
          <v-divider class="mb-1"></v-divider>

          <v-divider></v-divider>
        </v-responsive>


        <div></div>

        <v-btn
          
          color="grey"
          @click="gotoCreateAccount"
          outlined
          large
        >
            <span class="grey--text text--darken-1 font-weight-bold">
              Begin your journey with us
            </span>
        </v-btn>
      </v-container>

      <div class="py-12"></div>
    </section>
  </div>
</template>

<script>
 
  import {mapGetters} from 'vuex'

  export default {
    components: {
      
    },

    data: () => ({
      showTopSearch: 0,
      rating: 3,


      loading: false,
      items: [],
      search: null,
      model: null,
      selected: null,
      showResults: false,
    }),

    // async asyncData({$axios, dispatch}) {
    //   try {
    //     const detailsRes = await $axios.get('/details')
    //     const {data} = await $axios.get('/featuredSongs')
    //     return {featuredSongs: data, details: detailsRes.data}
    //   } catch (error) {
    //     return {featuredSongs: []}
    //   }
    // },

    computed: {
      ...mapGetters({

      })
    },
    methods: {
      async searchTest(v) {
        const {data} = await this.$axios.get(`/search/${v}?just-search=true`)
        return data
      },

      gotoCreateAccount() {
        this.$router.push('/sign-up')
      },
      async querySelections(v) {

        try {
          this.loading = true
          this.items = await this.searchTest(v)
          this.loading = false
        } catch (error) {
          this.loading = false
        }


      },
      loadSearch(query) {
        this.$router.push(`/songs/search/${query}`)
      }
    },

    watch: {
      search(val) {
        val && val !== this.select && this.querySelections(val)
      },

      model(val) {
        val && this.loadSearch(val)
      }
    },

  }
</script>

<style>

  .welcome-background {

    background-image: linear-gradient(#23a6d5, #0e7a91);
  }

</style>