<template>
  <router-view></router-view>
</template>

<script>
export default {
  name: 'App',
  async created() {
    await this.$store.dispatch('setData');
    this.$store.dispatch('setAudio', this.$route.params);
  },
  watch: {
    '$route' (to){
        this.$store.dispatch('setAudio', to.params);
    }
  }
}
</script>

<style lang='scss'>
* { 
  box-sizing: box-border;
  margin: 0;
  padding: 0;
  color: white;
  background: black;

  &::selection {
    color: red;
  }
}

body {
  min-height: 100vh;
  line-height: 1.3;

  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
