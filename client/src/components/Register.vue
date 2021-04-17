<template>
  <v-app>
    <v-main>
      <v-container>
        <v-row>
          <v-col class="borda rounded elevation-5 mt-10 text-center pb-5" md="4" offset-md="4">
            <v-toolbar flat dense dark>
              <v-toolbar-title>Register</v-toolbar-title>
            </v-toolbar>
            <div>
              <input class="my-5" type="email" name="email" v-model="email" placeholder="email" />
              <br>
              <input type="password" name="password" v-model="password" placeholder="password" />
              <br>
              <div class="error mt-3 p-5 rounded" v-html="error" />
              <br>
              <v-btn elevation="2" @click='register'>Register</v-btn>
            </div>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import AuthenticationService from '@/services/AuthenticationService'

export default {
  data () {
    return {
      email: '',
      password: '',
      error: null
    }
  },
  methods: {
    async register () {
      try {
        await AuthenticationService.register({
          email: this.email,
          password: this.password
        })
      } catch (error) {
        this.error = error.response.data.error
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.error {color:white;}
</style>
