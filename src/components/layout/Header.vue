<template>
  <nav class="navbar" role="navigation" aria-label="main navigation">
  <div class="navbar-brand">
    <a class="navbar-item" href="/">
      <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e9/Samsung_Internet_logo.svg/1200px-Samsung_Internet_logo.svg.png">
      
    </a>
    <h1 class="title">Code Challenge</h1>
  </div>
  <div id="navbarBasicExample" class="navbar-menu">
    <div class="navbar-start">
      <router-link to="/" class="navbar-item">Home</router-link>
      <router-link to="/admin" class="navbar-item" v-if="$auth.isAuthenticated">Admin</router-link>

      <div v-if="!$auth.loading">
        <!-- show login when not authenticated -->
        <a v-if="!$auth.isAuthenticated" @click="login" class="navbar-item"><strong>Log In</strong></a>
        <!-- show logout when authenticated -->
        <a v-if="$auth.isAuthenticated" @click="logout" class="navbar-item"><strong>Log Out</strong></a>
      </div>
    </div>
  </div>
</nav>
</template>

<script>
export default {
    name: 'Header',
    methods: {
    // Log the user in
    login() {
      this.$auth.loginWithRedirect();
    },
    // Log the user out
    logout() {
      this.$auth.logout({
        returnTo: window.location.origin
      });
    }
  }
}
</script>

<style>
  .title {
    margin-left: 10px;
    margin-top: 7px;
    color: white;
  }
  .navbar {
    background: #222;
  }
  .navbar-item {
    color: white;
  }
</style>