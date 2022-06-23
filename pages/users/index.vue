<template>
  <section>
    <h1>{{ pageTitle }}</h1>
    <ul>
      <li v-for="user in users"  :key="user.id">
        <a @click.prevent="openUser(user)" href="#">{{ user.name }} <p>City: {{user.address.city}} </p> </a>
      </li>

    </ul>
  </section>
</template>
<script>
// const {data} =  useAsyncData('users', () => fetch('https://jsonplaceholder.typicode.com/users'))
// console.log(data)

 export default {
  // async asyncData({ $axios }) {
  //   const users = await $axios.$get('https://jsonplaceholder.typicode.com/users')
  //  return  {users}
  // },
  async fetch({store}) {
    console.log(store.getters)
    if (store.getters['users/users'].length === 0) {
      await store.dispatch('users/fetch')
    }
  },
  data:() => ({
    pageTitle: 'Users page',
    // users: []
  }),

  computed: {
    users() {
      return this.$store.getters['users/users']
    }
  },

 // async mounted() {
 //   this.users = await this.$axios.$get('https://jsonplaceholder.typicode.com/users')
 //   console.log(this.users)
 //  },

  methods: {
    openUser(user) {
      console.log('USER ' + user)
      this.$router.push('/users/'+ user.id)
    }
}
}
</script>
