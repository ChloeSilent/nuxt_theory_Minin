<template>
  <section class="container">
    <h5>{{user.name}}</h5>
    <p>{{ user.phone }}</p>
    <p>{{ user.website }}</p>

  </section>
</template>

<script>
    export default {
        data: () => ({
            text: 'hey!'
        }),
        validate({params}) {
            console.log("params ", params);
            return /^\d+$/.test(params.id);
        },
        async asyncData({params, error, store}) {
            try {
                const user = await store.dispatch('users/fetchUserById', params.id)
                return {user}
            } catch (e) {
                error(e)
            }
        }
    }
</script>

<style>
</style>
