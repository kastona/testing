<template>
  <div>

<section class="grey lighten-5">
        <!-- Stack the columns on mobile by making one full-width and the other half-width -->
        <v-row>
          
          <v-col  cols="12" >
            <v-expand-transition>
            <FlashCard :news="latestStories[flashIndex].title"/>
            </v-expand-transition>
          </v-col>
        </v-row>
</section>


    <section class="grey lighten-5">
      <v-container>
        <!-- Stack the columns on mobile by making one full-width and the other half-width -->
        <v-row>

          <v-col cols="12" md="8">
            <BreakingBig :post="latestStories[0]" />
          </v-col>
          <v-col cols="12" md="4">
            <v-card color="secondary" class="white--text" height="400px">
              Ad should be placed here
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </section>

    <section id="featured">
      <div class="py-4"></div>

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
          <v-col
            v-for="story in latestStories.slice(1)"
            :key="story._id"
            cols="12"
            md="4"
            sm="6"
          >
            <PostCard :post="story" />
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
          <v-col
            v-for="video in videos"
            :key="video._id"
            cols="12"
            md="4"
            sm="6"
          >
            <VideoCard :post="video" />
          </v-col>
        </v-row>
      </v-container>
    </section>
  </div>
</template>

<script>
import { mapGetters } from "vuex";
import PostCard from "~/components/PostCard";
import VideoCard from "~/components/VideoCard";
import BreakingBig from "~/components/fob/BreakingBig";
import FlashCard from "~/components/FlashCard"
export default {
  components: {
    PostCard,
    VideoCard,
    BreakingBig,
    FlashCard
  },

  data: () => ({
    showTopSearch: 0,
    rating: 3,
    flashIndex: 0,
    reload: false,
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
      latestStories: "getLatestStories",
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

  mounted() {
    const self = this
    setInterval(function () {
      self.flashIndex +=1;
      if(self.flashIndex > 5) {
        self.flashIndex = 0;
      }

      self.reload = true
    }, 5000);
  }
};
</script>

<style>
.welcome-background {
  background-image: linear-gradient(#242525, #091518);
}
</style>