<template>
  <div>
    <h1>Search Github Users</h1>
    <input
      type="text"
      placeholder="enter the name you search"
      v-model="keyWord"
    />
    <button @click="searchUsers">Search</button>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Search-",
  data() {
    return {
      keyWord: "",
    };
  },
  methods: {
    searchUsers() {
      axios
        .get(`https://api.github.com/search/users?q=${this.keyWord}`)
        .then((result) => {
          this.$bus.$emit("getUser", result.data.items);
        })
        .catch((err) => {
          console.log(err.message);
        });
    },
  },
};
</script>

<style>
button {
  margin-left: 10px;
}
</style>
