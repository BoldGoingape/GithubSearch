<template>
  <div class="rwow">
    <!-- 展示用户咧表 -->
    <div class="card" v-for="user in info.users" :key="user.login">
      <a :href="user.html_url" target="_blank">
        <img :src="user.avatar_url" alt="" />
        <p class="card-text">{{ user.login }}</p>
      </a>
    </div>
    <!-- 展示欢迎词 -->
    <h1 v-show="info.isFirst">欢迎</h1>
    <!-- 展示加载中 -->
    <h1 v-show="info.isLoading">加载中。。。</h1>
    <!-- 错误信息 -->
    <h1 v-show="info.errMsg">{{ info.errMsg }}</h1>
  </div>
</template>

<script>
export default {
  name: "List-",
  data() {
    return {
      info: {
        isFirst: true,
        isLoading: false,
        errMsg: "",
        users: [],
      },
    };
  },
  mounted() {
    this.$bus.$on("getUser", (user) => {
      console.log(user);
      this.info = user;
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
