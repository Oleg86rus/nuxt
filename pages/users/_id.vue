<template>
  <section>
    <h1>{{ user.name }}</h1>
    <hr>
    <h3>{{ user.email }}</h3>
  </section>
</template>

<script>
export default {
  name: '_id',
  validate ({params}) {

    console.log('validate')
    return /^\d+$/.test(params.id)
  },
  async asyncData ({ $axios, params }) {
    const user = await $axios.$get('https://jsonplaceholder.typicode.com/users/' + params.id)
    return {user}
  }
}
</script>

<style scoped>

</style>
