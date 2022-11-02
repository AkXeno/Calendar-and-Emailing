<template>
  <div id="app">
    <AgendaDaymap />
    <EmailSystem />
  </div>
</template>

<script>
const width = window.innerWidth;
const height = window.innerHeight;
import AgendaDaymap from './components/AgendaDaymap.vue'
import EmailSystem from './components/EmailSystem.vue'

export default {
  name: 'App',
  components: {
    AgendaDaymap,
    EmailSystem
  },
  data() {
    return {
      stageSize: {
        width: width,
        height: height
      }
    };
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #3198ff;
  margin-top: 0px;
  background-color: #ffffff;
}
</style>
