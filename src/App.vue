<template>
  <div id="app">
    <GNB/>
    <router-view/>
  </div>
</template>

<script>
import GNB from '@/components/GNB.vue';

export default {
  name: 'App',
  components: {
    GNB
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
