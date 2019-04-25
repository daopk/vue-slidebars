<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" @click="show = true">
    <p>Click the Logo to show the slidebar</p>
    <SlideBars v-model="show" position="left">
      <ul>
        <li>Menu 1</li>
        <li>Menu 2</li>
      </ul>
    </SlideBars>
  </div>
</template>

<script>
import SlideBars from './components/slidebars.vue'

export default {
  name: 'app',
  components: {
    SlideBars
  },
  data: () => ({
    show: false
  })
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
