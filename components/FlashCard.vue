<template>
  <v-card >
      <v-container>
          <v-card-text> <v-chip label color="secondary" class="mr-4">Flash News</v-chip> {{ news }} </v-card-text>
      </v-container>
  </v-card>
</template>
<script>
export default {
  props: ["news"],
};
</script>