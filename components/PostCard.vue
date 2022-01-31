<template>
  <v-card
    :ripple="false"
    max-width="400px"
    :href="`/news/${post._id}/${post.seoTitle}`"
    class="mx-auto"
  >
    <v-img
      class="white--text align-end"
      height="250px"
      gradient=" rgba(0,0,0,0.2), rgba(0,0,0,1)"
      :src="post.coverUrl"
    >
      <v-container>
        <v-row>
          <v-col cols="12">
            <v-card-text  class="text-capitalize py-0"><div :class="$vuetify.breakpoint.smAndDown? 'subtitle-1': 'text-justify headline'">{{ post.title }}</div></v-card-text>
            <v-card-text>
              <v-row class="px-4 grey--text" align="center">
                <v-avatar size="24" class="mr-2">
                  <v-icon small color="white"
                    >mdi-clock-time-four-outline</v-icon
                  >
                </v-avatar>

                <span>{{ $moment(post.createdAt).format("ll") }}</span> <v-spacer></v-spacer><v-chip label x-small color="error">{{ post.tags[0] }}</v-chip>
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
  data: () => ({
    show: false,
  }),
  props: ["post"],
};
</script>