<template>
  <!-- https://github.com/tyson-tlo/vue3-vuex-shopping-cart -->
  <div id="nav">
    <router-link to="/">Home</router-link>
    <router-link to="/cart" class="pl-4">Cart</router-link>
  </div>
  <router-view />
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>

<script>
export default {
  mounted() {
    this.$store.commit("updateCartFromLocalStorage");
  },
  setup() {
    return {};
  },
};
</script>
