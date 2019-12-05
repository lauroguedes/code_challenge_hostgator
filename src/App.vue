<template>
  <div id="app">
    <Header />
    <Banner />
    <Plans />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Banner from './components/Banner.vue'
import Plans from './components/Plans.vue'

export default {
  name: 'app',
  components: {
    Header,
    Banner,
    Plans
  }
}
</script>
