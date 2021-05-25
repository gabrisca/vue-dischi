<template>
  <div>
    <select class="form-select mc_form mt-4" aria-label="Genre selection">
      <option 
      v-for="(genre, index) in genresArray"
      :key="index"
      selected>{{genre}}</option>
    </select>
  </div>
</template>


<script>
// importo in Main axios per la chiamata API
import axios from "axios";

export default {
  name: 'SelectGenre',
  data(){
    return {
      // creo un array vuoto dove caricare i generi degli album
      genresArray: ['Select your favorite music',],
    }
  },
  created() {
    // chiamata API 
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((res) => {
        res.data.response.forEach((album)=> {
          // forEach su ogni album dell'array
          // se l'array non contiene il genere dell'album faccio un pudh nell'array genresArray
          if(!this.genresArray.includes(album.genre)){
            this.genresArray.push(album.genre)
          }
          // .sort sull'array restituisce l'ordine delle stringhe invertito 
          // mi serve per visualizzare l'option di default 'Select your music'
          this.genresArray.sort()
        })
        console.log(this.genresArray);
      })
      .catch((error) => {
        console.log(error);
      });
  },
}
</script>

<style lang="scss" scoped>
  .mc_form {
    width: 300px;
    margin: 0 auto;
  }
</style>