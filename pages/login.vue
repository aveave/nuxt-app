<template>
    <form class="login-form" @submit.prevent="onSubmit">
        <h1>Login page</h1>
        <div v-if="$route.query.message" class="alert alert-danger">
          Need login
        </div>
        <div class="form-group">
          <label for="exampleInputEmail1">Email address</label>
          <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp">
          <small id="emailHelp" class="form-text text-muted">We'll never share your email with anyone else.</small>
        </div>
        <div class="form-group">
          <label for="exampleInputPassword1">Password</label>
          <input type="password" class="form-control" id="exampleInputPassword1">
        </div>
        <div class="form-group form-check">
          <input type="checkbox" class="form-check-input" id="exampleCheck1">
          <label class="form-check-label" for="exampleCheck1">Check me out</label>
        </div>
        <button type="submit" class="btn btn-primary">Submit</button>
        <nuxt-link to="/">Back to Home page</nuxt-link>
      </form>
</template>

<script>
    export default {
        layout: 'empty',
        
        methods: {
          onSubmit() {
            this.$store.dispatch('login');
            this.$router.push('/');
          }
        }
    }
</script>

<style>
    .login-form {
        width: 500px;
        margin: 0 auto;
    }

    .login-form a {
        float: right;
    }
</style>