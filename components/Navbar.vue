<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <a class="navbar-brand" href="#">Navbar</a>
    <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav"
      aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNav">
      <ul class="navbar-nav">
        <li class="nav-item active">
          <nuxt-link exact active-class="active" class="nav-link" to="/">Home <span class="sr-only">(current)</span>
          </nuxt-link>
        </li>
        <li class="nav-item">
          <nuxt-link active-class="active" no-prefetch class="nav-link" to="/about">About</nuxt-link>
        </li>
        <li class="nav-item">
          <nuxt-link active-class="active" class="nav-link" to="/todo">Todos</nuxt-link>
        </li>
        <li class="nav-item">
          <nuxt-link active-class="active"  v-if="!hasToken" class="nav-link" to="/login">Login</nuxt-link>
        </li>
        <li class="nav-item">
          <a href="#" @click.prevent="logout" v-if="hasToken" class="nav-link">Logout</a>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
  export default {

    computed: {
      hasToken() {
        return this.$store.getters.hasToken;
      }
    },

    methods: {
      logout() {
        this.$store.dispatch('logout');
        this.$router.push('/login')
      }
    }
  }
</script>