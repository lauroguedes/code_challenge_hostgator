<template>
  <div id="app">
    <Header />
    <Banner />
    <Plans />
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Header from './components/Header.vue'
import Banner from './components/Banner.vue'
import Plans from './components/Plans.vue'

export default {
  name: 'app',
  components: {
    HelloWorld,
    Header,
    Banner,
    Plans
  }
}
</script>

<style lang="scss">

</style>
