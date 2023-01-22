<template>
  <div>
    <a class="navbar-brand" href="/">Nuxt</a>
    <div class="">
      <ul class="nav mr-auto">
        <li class="nav-item">
          <nuxt-link exact active-class="active" class="nav-link" to="/">
            Home
          </nuxt-link>
        </li>
        <li class="nav-item">
          <nuxt-link active-class="active" class="nav-link" to="/about">
            About
          </nuxt-link>
        </li>
        <li class="nav-item">
          <nuxt-link active-class="active" class="nav-link" to="/users">
            users
          </nuxt-link>
        </li>
        <li class="nav-item" v-if="!hasToken">
          <nuxt-link active-class="active" class="nav-link" to="/login">
            login
          </nuxt-link>
        </li>
        <li class="nav-item" v-else>
          <a @click.prevent="logout" class="nav-link" href="#">
            logout
          </a>
        </li>
      </ul>
    </div>

  </div>
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

<style scoped>
.nav {
  display: flex;
  align-items: center;
}

.navbar {
  width: 350px;
  margin-left: 150px;
}
</style>
