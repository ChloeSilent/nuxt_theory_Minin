<template>
  <section class="container">
    <form @submit.prevent="onSubmit">
      <h1>Login</h1>
      <div class="form-group">
        <input type="text" class="form-control">
      </div>
      <div class="form-group">
        <input type="password" class="form-control">
      </div>
      <button class="btn btn-primary" type="submit">Submit</button>
    </form>
    <p>
      <nuxt-link exact class="nav-link" active-class="active" to="/">Home</nuxt-link>
    </p>
  </section>
</template>

<script>
    export default {
        layout: 'empty'
        , methods: {
            onSubmit() {
                this.$store.dispatch('login');
                this.$router.push('/');
            }
        }

    }
</script>

<style scoped>
  form {
    width: 400px;
  }
</style>
