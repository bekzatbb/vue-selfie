<template>
  <div id="app">
    <Selfie @picture-taken="imageSrc = $event" />

    <img :src="imageSrc" />
  </div>
</template>

<script>
import Selfie from './components/Selfie.vue'

export default {
  name: 'App',
  components: {
    Selfie
  },
  data() {
    return {
      imageSrc: null
    }
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
  margin-top: 60px;
}
</style>
