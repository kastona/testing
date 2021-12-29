<template>
  <v-card :href="`/news/${post._id}/${post.seoTitle}`"  class="mx-auto" max-width="400">
    <v-img
      class="white--text align-end"
      height="200px"
      gradient=" rgba(0,0,0,0.2), rgba(0,0,0,1)"
      :src="post.coverUrl"
    >
      <v-card-title>{{ post.title }}</v-card-title>
    </v-img>
    <v-card-actions>

      <v-spacer></v-spacer>
      <v-btn :href="`/news/${post._id}/${post.seoTitle}`" color="orange lighten-2" text> Read Story </v-btn>

    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  data: () => ({
     show: false
   }),
  props: ["post"],
};
</script>