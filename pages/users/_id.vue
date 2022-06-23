<template>
  <section>
<!--    <h1>User {{$route.params.id}}</h1>-->
    <h1>{{user.username}}</h1>
    <h3>email: {{user.email}}</h3>
    <h3>phone: {{user.phone}}</h3>
  </section>

</template>
<script>
export default {
 validate({params}) {
   return /^\d+$/.test(params.id)
 },
  async asyncData({ $axios, params }) {
    const user = await $axios.$get('https://jsonplaceholder.typicode.com/users/'+ params.id)
    return  {user}
  },
}
</script>
