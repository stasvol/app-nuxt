<template>
  <nav class="navbar navbar-expand-lg bg-dark">
    <div class="container-fluid ">
      <a class="navbar-brand " href="#">NUXT SSR</a>
      <div class="collapse navbar-collapse bg-light " >
        <ul class="navbar-nav me-auto mb-2 mb-lg-0 ">
          <li class="nav-item ">
            <nuxt-link no-prefetch exact to="/" class="nav-link " active-class="active">
              Home
            </nuxt-link>
<!--            <a class="nav-link " href="/">Home</a>-->
          </li>
          <li class="nav-item">
            <nuxt-link to="/about" class="nav-link" active-class="active">
              About
            </nuxt-link>
          </li>
          <li class="nav-item">
            <nuxt-link to="/users" class="nav-link" active-class="active">
              Users
            </nuxt-link>
          </li>
          <li class="nav-item" v-if="!hasToken">
            <nuxt-link to="/login" class="nav-link" active-class="active">
              Login
            </nuxt-link>
          </li>
          <li class="nav-item" v-else>
            <a @click.prevent="logout" href="#" class="nav-link">
              Logout
            </a>
          </li>

        </ul>
      </div>
    </div>
  </nav>
</template>
<script>
export default {
  computed: {
    hasToken() {
      return this.$store.getters.hasToken
    }
  },
  methods: {
    logout() {
      this.$store.dispatch('logout')
      this.$router.push('/login')
    }
  }
}
</script>
