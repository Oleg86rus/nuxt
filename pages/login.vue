<template>
  <section>
    <div v-if="$route.query.message" class="alert alert-danger mb-3">
      Need login first
    </div>
    <form @submit.prevent="onSubmit">
      <h1>Login Page</h1>
      <div class="form-group">
        <input type="text"/>
      </div>

      <p>
        <nuxt-link to="/">To home page</nuxt-link>
      </p>
      <button class="btn btn-primary" type="submit">Login</button>
    </form>
  </section>
</template>

<script>
export default {
  name: 'login',
  layout: 'empty',
  methods: {
    onSubmit() {
      this.$store.dispatch('login')
      this.$router.push('/')
    }
  }
}
</script>

<style scoped>
  form {
    width: 600px;
    margin: 0 auto;
  }
  section {
    width: 600px;
    margin: 0 auto;
  }
</style>
