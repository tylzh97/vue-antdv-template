<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view />
    <a-button type="primary" @click="handleClick">Hello</a-button>
  </div>
</template>

<script>
export default {
  name: 'App',
  methods: {
    handleClick() {
      this.$requests
        ._get('http://ip-api.com/json', { lang: 'zh-CN' })
        .then(res => {
          this.$message.success(`您好, 来自 ${res.regionName}省 ${res.city} 的朋友!`);
          console.log('reqTest: ', res);
        });
    },
  },
};
</script>

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
