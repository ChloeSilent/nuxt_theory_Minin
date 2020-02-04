<template>
  <section class="container">
    <h5>{{ pageTitle }}</h5>
    <ul>
      <li v-for="user in users" :key="user.id">
        <a href="#" @click.prevent="goTo(user)">
          <p>{{ user.name }}</p>
        </a>
      </li>
    </ul>
  </section>
</template>

<script>
    import error from "../../layouts/error";

    export default {
        // async fetch({store, error}) {
        //     try {
        //         if(store.getters['users/users'].length === 0 ){
        //             await store.dispatch('users/fetchUsers')
        //         }
        //     } catch (e) {
        //         error(e)
        //     }
        // },

        middleware: ['auth'],// они вызываются по очереди слева направо,

        data: () => ({
            pageTitle: 'This is Users page'
        }),
        methods: {
            goTo(user) {
                this.$router.push('/users/' + user.id)
            }
        },
        computed: {
            users() {
                return this.$store.getters['users/users'] // первый параметр это модуль, а второй название геттера
            }
        }
    }
</script>
