<template>
  <div>
    <section class="welcome-background">
      
      <v-container style="min-height: 50vh" fluid fill-height>
        <v-layout flex align-center justify-center>
          
          <v-flex class="white--text text-center" xs12 md8 sm6>
            
<div style="color: white;" :class="$vuetify.breakpoint.mdAndUp? 'text-h1': 'text-h3'"  class=" font-weight-light">
FOB NEWS
</div>


            <h2 style="color: white" class="banner2-title font-weight-light">
              
              Your
              <span class="font-italic font-weight-bold">
                Fair, Objective & Balanced News
              </span>
            </h2>
            </v-responsive>
          </v-flex>
        </v-layout>
      </v-container>
    </section>

    <section id="featured">
      <div class="py-12"></div>

      <v-container light class="text-center">
        <h2 class="primary--text text--lighten-1 font-weight-bold mb-3">
          Headlines
        </h2>

        <v-responsive class="mx-auto" width="56">
          <v-divider
            v-if="!$vuetify.breakpoint.smAndDown"
            class="mb-1"
          ></v-divider>
        </v-responsive>

        <v-row>
          <v-col v-for="story in topStories" :key="story._id" cols="12" md="4" sm="6">
            <PostCard :post="story"/>
          </v-col>
        </v-row>
      </v-container>
    </section>



  <section id="videos">
      <div class="py-12"></div>

      <v-container light class="text-center">
        <h2 class="primary--text text--lighten-1 font-weight-bold mb-3">
          Videos
        </h2>

        <v-responsive class="mx-auto" width="56">
          <v-divider
            v-if="!$vuetify.breakpoint.smAndDown"
            class="mb-1"
          ></v-divider>
        </v-responsive>

        <v-row>
          <v-col v-for="video in videos" :key="video._id" cols="12" md="4" sm="6">
            <VideoCard :post="video"/>
          </v-col>
        </v-row>
      </v-container>
    </section>


  <section id="featured">
      <div class="py-12"></div>

      <v-container light class="text-center">
        <h2 class="primary--text text--lighten-1 font-weight-bold mb-3">
          Top News
        </h2>

        <v-responsive class="mx-auto" width="56">
          <v-divider
            v-if="!$vuetify.breakpoint.smAndDown"
            class="mb-1"
          ></v-divider>
        </v-responsive>

        <v-row>
          <v-col v-for="story in latestStories" :key="story._id" cols="12" md="4" sm="6">
            <PostCard :post="story"/>
          </v-col>
        </v-row>
      </v-container>
    </section>
  </div>
</template>

<script>
import { mapGetters } from "vuex";
import PostCard from '~/components/PostCard'
import VideoCard from '~/components/VideoCard'
export default {
  components: {
    PostCard,
    VideoCard
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
      videos: "getTopVideos",
      topStories: "getTopStories",
      latestStories: "getLatestStories"
    }),
  },
  methods: {
    async searchTest(v) {
      const { data } = await this.$axios.get(`/search/${v}?just-search=true`);
      return data;
    },

    gotoCreateAccount() {
      this.$router.push("/sign-up");
    },
    async querySelections(v) {
      try {
        this.loading = true;
        this.items = await this.searchTest(v);
        this.loading = false;
      } catch (error) {
        this.loading = false;
      }
    },
    loadSearch(query) {
      this.$router.push(`/songs/search/${query}`);
    },
  },

  watch: {
    search(val) {
      val && val !== this.select && this.querySelections(val);
    },

    model(val) {
      val && this.loadSearch(val);
    },
  },
};
</script>

<style>
.welcome-background {
  background-image: linear-gradient(#242525, #091518);
}
</style>