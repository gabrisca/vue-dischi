<template>
  <div class="container">
    <div class="row">
      <Album 
      v-for="(album, index) in albums"
      :key="index"
      :album = "album"
      />
    </div>
  </div>
</template>

<script>
import Album from './Album.vue'
import axios from 'axios'

export default {
  components: { 
    Album
 },
 data(){
   return {
     axios,
     albums: [],
   }
 },
 created(){
   axios.get('https://flynn.boolean.careers/exercises/api/array/music')
   .then(res =>{
     this.albums = res.data.response
     console.log(this.albums);
   })
   .catch(error =>{
     console.log(error);
   })
 }
}
</script>

<style lang="scss" scoped>

</style>