<template>
  <v-card  :ripple="false" :href="`/news/${post._id}/${post.seoTitle}`" class="mx-auto">
    <v-img
      min-height="300px"
      class="white--text align-end"
      gradient=" rgba(0,0,0,0.2), rgba(0,0,0,1)"
      :src="post.coverUrl"
    >
      <v-container>
        <v-row>
          <v-col cols="12">
              <v-card-text>
                  <v-chip label small color="error">Breaking News</v-chip>
              </v-card-text>
            <v-card-title>{{ post.title }}</v-card-title>
              <v-card-text>

                  <v-row
      class="px-4 grey--text"
      align="center"
    >
      <v-avatar
        size="24"
        class="mr-2"
      >
        <v-icon small color="white">mdi-clock-time-four-outline</v-icon>
      </v-avatar>

      <span>{{$moment(post.createdAt).format('ll')}}</span>
    </v-row>
                  
                </v-card-text>
          </v-col>
        </v-row>
      </v-container>
    </v-img>
  </v-card>
</template>

<script>
export default {
  props: ["post"],
};
</script>