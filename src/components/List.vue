<template>
  <div class="rwow">
    <div class="card" v-for="user in users" :key="user.login">
      <a :href="user.html_url" target="_blank">
        <img :src="user.avatar_url" alt="" />
        <p class="card-text">{{ user.login }}</p>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: "List-",
  data() {
    return {
      users: [],
    };
  },
  mounted() {
    this.$bus.$on("getUser", (user) => {
      console.log(user);
      this.users = user;
    });
  },
};
</script>

<style>
.rwow {
  margin-top: 10px;
}
img {
  width: 250px;
  height: 150px;
}
.card {
  float: left;
  width: 30.33%;
  padding: 0.75rem;
  margin-bottom: 2rem;
  border: 1px solid #efefef;
  text-align: center;
}
.card > img {
  margin-bottom: 0.5rem;
  border-radius: 100px;
}
.card-text {
  font-size: 85%;
}
</style>
