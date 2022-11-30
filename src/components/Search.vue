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
      this.$bus.$emit("getUser", {
        isFirst: false,
        isLoading: true,
        errMsg: "",
        users: [],
      });
      axios
        .get(`https://api.git11hub.com/search/users?q=${this.keyWord}`)
        .then((result) => {
          this.$bus.$emit("getUser", {
            isLoading: false,
            errMsg: "",
            users: result.data.items,
          });
        })
        .catch((err) => {
          console.log(err.message);
          this.$bus.$emit("getUser", {
            isLoading: false,
            errMsg: err.message,
            users: [],
          });
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
