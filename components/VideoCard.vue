<template>
  <v-card class="mx-auto" max-width="344">
    <video-player :src="post.coverUrl"/>

    <v-card-title> {{post.title}} </v-card-title>

    <v-card-actions>
      <v-btn :href="`/news/${post._id}/${post.seoTitle}`" color="orange lighten-2" text> Open </v-btn>
    </v-card-actions>
  </v-card>
</template>

  <script>
import VideoPlayer from "nuxt-video-player";
require("nuxt-video-player/src/assets/css/main.css");
export default {
   data: () => ({
     show: false
   }),
    components: {
        VideoPlayer
    },

    props: ['post']
};
</script>