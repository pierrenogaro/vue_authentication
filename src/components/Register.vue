<template>
  <form @submit.prevent="register">
    <h2>Register</h2>
    <input v-model="email" type="email" placeholder="Email" required />
    <input v-model="password" type="password" placeholder="Password" required />
    <button type="submit">Register</button>
  </form>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Register',
  data() {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    async register() {
      try {
        const response = await axios.post('https://backend.imatrythis.com/registration', {
          email: this.email,
          password: this.password
        })

        if (response.data.success) {
          alert('Inscription réussie !')
          this.$router.push('/login')
        }
      } catch (error) {
        console.error(error)
      }
    }
  }
}
</script>