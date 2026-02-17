<template>
  <div>
    <h1>{{ message || 'Chargement...' }}</h1>
    <button @click="logout">Déconnexion</button>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      message: ''
    }
  },
  async mounted() {
    const token = localStorage.getItem('authToken')

    if (!token) {
      this.$router.push('/login')
      return
    }

    console.log('Token:', token)

    try {
      const response = await axios.get('https://backend.imatrythis.com/api/hello', {
        headers: { 'Authorization': `Bearer ${token}` }
      })
      this.message = response.data.message
    } catch (error) {
      if (error.response?.status === 401) {
        localStorage.removeItem('authToken')
        localStorage.removeItem('userEmail')
        this.$router.push('/login')
      }
    }
  },
  methods: {
    logout() {
      localStorage.removeItem('authToken')
      localStorage.removeItem('userEmail')
      this.$router.push('/login')
    }
  }
}
</script>