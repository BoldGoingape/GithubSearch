<template>
  <div id="app">
    <SearchVue></SearchVue>
    <ListVue> </ListVue>
  </div>
</template>

<script>
import ListVue from "./components/List.vue";
import SearchVue from "./components/Search.vue";
export default {
  name: "App",
  components: {
    ListVue,
    SearchVue,
  },
};
</script>

<style>
#app {
}
</style>
