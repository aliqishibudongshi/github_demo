<template>
  <div class="container">
    <SearchUser/>
    <ListUser/>
  </div>
</template>

<script>
import ListUser from './components/List.vue';
import SearchUser from './components/Search.vue';
export default {
  name: 'App',
  components: {
    SearchUser,
    ListUser
  }
}
</script>

<style>

</style>
