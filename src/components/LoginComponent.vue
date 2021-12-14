<template>
  <v-container>
    <v-card max-width="450px" height="430px" class="mx-auto">
      <v-card-text class="pb-2">
         <v-progress-linear
          :active="loading"
          :indeterminate="loading"
          absolute
          top
          color="green"
        ></v-progress-linear>
        <p class="text-subtitle-1 text-center mt-2 primary-text-2">
          Sign in to your account
        </p>
      </v-card-text>
      <v-card-text class="pb-1">
        <v-text-field outlined placeholder="Username"></v-text-field>
        <v-text-field outlined placeholder="Password"></v-text-field>
        <v-row>
          <v-col>
            <v-checkbox v-model="checkbox" label="Remember Me "></v-checkbox>
          </v-col>
          <v-col>
           <!-- <a href="javascript:void(0);" @click="showForgotPWDForm">Forgot Password?</a>-->
           <router-link to="/forgotpassword">Forgot Password?</router-link>
          </v-col>
        </v-row>
        <v-card-actions>
          <v-btn block depressed color="success" 
           @click="loading = true"
           style="min-height: 50px">
            Login
          </v-btn>
        </v-card-actions>
      </v-card-text>
    </v-card>
    <br />
    <v-card max-width="450px" height="60px" class="mx-auto">
      <p class="primary-text-1 ls-08 text-center text-subtitle-2 pa-3 ml-3">
        Don't have an account? <router-link to="/register">Create One</router-link>
      </p>
    </v-card>
  </v-container>
</template>

<script>
export default {
  name: "Login",
  data: () => ({
    loading: false,
  }),

  watch: {
    loading (val) {
      if (!val) return

      setTimeout(() => (this.loading = false), 3000)
    },
  },

  methods: {
    showForgotPWDForm() {
      this.$emit("show-forgot-password");
    },
  },
};
</script>

<style scoped>
.container {
  padding: 170px;
}
</style>
