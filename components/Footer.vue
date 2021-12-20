<template>
  <v-footer
    dark
    padless
  >
    <v-card
      flat
      tile
      style="width: 100%"
      class="secondary darken-2 white--text text-center"
    >
      <v-card-text>
        <v-btn
          class="mx-4 white--text"
          icon
          link
          target="_blank"
          href="https://web.facebook.com/"
        >
          <v-icon size="24px">mdi-facebook</v-icon>
        </v-btn>
 <v-btn
          class="mx-4 white--text"
          icon
          link
          target="_blank"
          href="https://www.youtube.com/"
        >
          <v-icon size="24px">mdi-youtube</v-icon>
        </v-btn>

<v-btn
          class="mx-4 white--text"
          icon
          link
          target="_blank"
          href="https://www.twitter.com/"
        >
          <v-icon size="24px">mdi-twitter</v-icon>
        </v-btn>

<v-btn
          class="mx-4 white--text"
          icon
          nuxt
          to="/login"
        >
          <v-icon size="24px">mdi-account</v-icon>
        </v-btn>
      </v-card-text>

      <v-card-text class="white--text pt-0">
        <span class="px-5"><v-icon>mdi-phone</v-icon> 0803887788043</span>

        <span><v-icon>mdi-email</v-icon> email@gmail.com</span>
      </v-card-text>

      <v-divider></v-divider>

      <v-card-text class="white--text">
        &copy; {{ new Date().getFullYear() }} — <strong>FOB NEWS</strong>
      </v-card-text>
    </v-card>
  </v-footer>
</template>
