<template>
  <section>
    <div v-if="$route.query.message" class="alert alert-danger mb-3">
      LOGIN   FIRST  NEED
    </div>
    <form @submit.prevent="onSubmit">
      <h1>Login page</h1>
      <div class="form-group">
        <input type="text" class="form-control">
      </div>
      &nbsp;
      <p>
        <nuxt-link to="/">To home page</nuxt-link>
      </p>

      <button class="btn btn-primary" type="submit">Login</button>
    </form>
  </section>
</template>
<script>
export default {
  layout: 'auth',
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
  width: 30rem;
  margin: 0 auto;
}
</style>
