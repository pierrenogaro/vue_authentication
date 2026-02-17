<template>
  <div>
    <nav>
      <router-link to="/login">Login</router-link> |
      <router-link to="/register">Register</router-link>
    </nav>
    <router-view />
  </div>
</template>

<style>
body {
  font-family: Arial, sans-serif;
  background-color: #201f1f;
  margin: 0;
  padding: 20px;
}

nav {
  text-align: center;
  margin-bottom: 30px;
}

nav a {
  color: #007bff;
  text-decoration: none;
  margin: 0 10px;
  font-size: 18px;
}

form {
  background: white;
  padding: 30px;
  border-radius: 8px;
  max-width: 400px;
  margin: 0 auto;
}

input {
  width: 100%;
  padding: 12px;
  margin-bottom: 15px;
  border: 1px solid #ddd;
  border-radius: 4px;
  box-sizing: border-box;
}

button {
  width: 100%;
  padding: 12px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
</style>