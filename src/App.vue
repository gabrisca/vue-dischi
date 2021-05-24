<template>
  <div id="app">
    <Header />
  </div>
</template>

<script>
import axios from 'axios'
import Header from './components/Header.vue'

export default {
  name: 'App',
  components: {
    Header
  },
data(){
  return {
    axios,
  }
},
}
</script>

<style lang="scss">
// importo il foglio di stile general.scss
  @import '@/assets/style/general';
</style>
