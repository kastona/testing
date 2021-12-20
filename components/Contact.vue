<template>
  <div>
    <div class="mini-spacer">
      <v-container>
        <!-- -----------------------------------------------
            Start Contact Form
        ----------------------------------------------- -->
        <v-row justify="center">
          <v-col cols="12" sm="10" md="12" lg="8">
            <div>
              <h4 class="font-weight-medium contact-title mt-0">
                For more information, contact us using the form below
              </h4>
              <form>
                <v-row class="mt-15">
                  <v-col cols="12" md="6" class="py-0">
                    <v-text-field
                      label="Name"
                      outlined
                      v-model="message.name"
                      placeholder="Name"
                    ></v-text-field>
                  </v-col>
                  <v-col cols="12" md="6" class="py-0">
                    <v-text-field
                      label="Email"
                      outlined
                      type="email"
                      v-model="message.email"
                      placeholder="Email"
                    ></v-text-field>
                  </v-col>
                  <v-col cols="12" class="py-0">
                    <v-textarea
                      name="message"
                      outlined
                      v-model="message.message"
                      label="Message"
                      rows="3"
                    ></v-textarea>
                  </v-col>
                </v-row>
                <v-btn
                  @click="sendMessage"
                  class="btn-custom-md btn-danger-gradient"
                  outlined
                  elevation="0"
                  :loading="loading"
                >
                  Submit
                </v-btn>
              </form>
            </div>
          </v-col>
        </v-row>
        <v-snackbar
      v-model="successfulSnackbar"
      :multi-line="multiLine"
    >
      Your message has been sent!

      <template v-slot:action="{ attrs }">
        <v-btn
          color="red"
          text
          v-bind="attrs"
          @click="successfulSnackbar = false"
        >
          Close
        </v-btn>
      </template>
    </v-snackbar>
      </v-container>
    </div>
  </div>
</template>
<script>
export default {
  name: "Contact",
  data() {
    return {
      loading: false,
      successfulSnackbar: false,
      message: {
        name: "",
        email: "",
        message: ""
      }
    };
  },
  methods: {
    async sendMessage() {
      this.loading = true

      try {
        const data = await this.$axios.post('/messages', this.message)
        this.loading = false
        this.successfulSnackbar = true;
        this.message = {
          name: '',
          email: '',
          message: ''
        }

        console.log(data)
      }catch(error) {
        console.log(error.message)
      }
    }
  },
};
</script>
