<template>
  <div>
    <section class="jumbotron">
      <h3 class="jumbotron-heading">Search Github Users</h3>
      <div>
        <input
        type="text"
        placeholder="enter the name you search"
        v-model="keyword"
        />&nbsp;<button @click="searchUsers">Search</button>
      </div>
    </section>
  </div> 
</template>

<script>
import axios from "axios";
export default {
  name: "SearchUser",
  data() {
    return {
      keyword: ""
    }
  },
  methods: {
    searchUsers(){
      // 请求前数据变化，主要变化isFirst
      this.$bus.$emit("updateDataList", {isFirst: false, isLoading: true, errMsg: "", users: []});
      axios.get(`https://api.github.com/search/users?q=${this.keywords}`)
      .then((result) => {
        this.$bus.$emit("updateDataList", {isLoading: false, errMsg: "", users: result.data.items})
      }).catch((err) => {
        this.$bus.$emit("updateDataList", {isLoading: false, errMsg: err.message, users: []})
      });
    }
  },
}
</script>

<style>

</style>