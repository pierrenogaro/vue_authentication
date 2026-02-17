<template>
  <form @submit.prevent="login">
    <h2>Login</h2>
    <input v-model="username" type="text" placeholder="Email" required />
    <input v-model="password" type="password" placeholder="Password" required />
    <button type="submit">Login</button>
  </form>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Login',
  data() {
    return {
      username: '',
      password: ''
    }
  },
  methods: {
    async login() {
      try {
        const response = await axios.post('https://backend.imatrythis.com/api/login_check', {
          username: this.username,
          password: this.password
        })

        if (response.data.token) {
          localStorage.setItem('authToken', response.data.token)
          localStorage.setItem('userEmail', this.username)
          this.$router.push('/hello')
        }
      } catch (error) {
        console.error(error)
      }
    }
  }
}
</script>