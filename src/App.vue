<template>
  <div id="app">
    <div class="container">
      <div class="row">
        <div class="col-md-6">
          ciao
        </div>
        <div class="col-md-6">
          ciao
        </div>
        <div class="col-md-6">
          ciao
        </div>
        <div class="col-md-6">
          ciao
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'App',
  components: {

  },
data(){
  return {
    axios,
  }
},
// created(){
//   axios.get('https://flynn.boolean.careers/exercises/api/array/music')
//   .the(risp =>{
//     console.log(risp.data.title);
//   })
//   .catch(error =>{
//     console.log(error);
//   })
// },
}
</script>

<style lang="scss">
  @import '@/assets/styles/general'
</style>
