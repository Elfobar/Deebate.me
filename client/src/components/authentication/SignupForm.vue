<template>
  <div class="form-container">
    <div
      style="
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        width: 100%;
      "
    >
      <b-card-title style="color: #007769" class=".rubik-text fw-semibold"
        >One Step Away! 🎉</b-card-title
      >
      <b-form @submit.prevent="signup" class="form" style="width: 100%;">
        <b-input type="email" v-model="user.email" placeholder="Email" />
        <b-input type="text" v-model="user.username" placeholder="@Username" />
        <b-input
          type="text"
          v-model="user.firstname"
          placeholder="First Name"
        />
        <b-input type="text" v-model="user.lastname" placeholder="Last Name" />
        <b-input
          type="password"
          v-model="user.password"
          placeholder="Password"
        />
        <b-button type="submit" class="button">Sign up</b-button>
      </b-form>
      <div class="flex flex-column column-gap-4 text-center">
        <p class="small fw-medium">
          Already have an account?
          <router-link to="/login" style="text-decoration: none"
            >Log in</router-link
          >
        </p>
        <p class="small fw-medium alert-message">{{ message }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import { Api } from '@/api/v1/Api.js'

export default {
  name: 'authentication',
  data() {
    return {
      user: {
        email: '',
        password: ''
      },
      message: ''
    }
  },
  methods: {
    async signup() {
      try {
        const response = await Api.post(
          '/auth/signup',
          {
            emailAddress: this.user.email,
            username: this.user.username,
            firstName: this.user.firstname,
            lastName: this.user.lastname,
            password: this.user.password
          }
        )

        // Handle the response, save the token if necessary
        console.log('Signup successful:', response.data)
        this.message = response.data.message || 'Signup successful!'

        // Redirect the user to the home page
        this.$router.push('/login')
      } catch (error) {
        // Handle errors and show an error message
        this.message =
          error.response && error.response.data.message
            ? error.response.data.message
            : 'Sign up failed, please try again.'
        console.error('Sign up failed:', this.message)
      }
    }
  }
}
</script>

<style>
.form-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}

.form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: fit-content;
  width: 500px;
  padding: 20px;
  gap: 20px;
}

.button {
  width: 100%;
  background-color: #007769;
  font-weight: bold;
  border: none;
}

.button:hover {
  background-color: #014a4a;
}

.button:active {
  background-color: #007769;
}

.button:focus {
  background-color: #007769;
}

.alert-message {
  color: red;
}
</style>
