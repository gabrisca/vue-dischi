<template>
  <div class="container mt-5 text-center">
    <!-- salvo in un div con condizione !loading il mio contenuto -->
    <div 
    v-if="!loading"
    class="row d-flex justify-content-center">
      <Album 
      v-for="(album, index) in albums" 
      :key="index" 
      :album="album"
       />
    </div>
    <!-- se loading è true mostro Loader con incola caricamento pagina -->
      <Loader 
      v-else
      title="Spotify"
      />
  </div>
</template>

<script>
// importo in Main axios per la chiamata API
import axios from "axios";
// importo in Main Album
import Album from "./Album.vue";
// importo in Main Loader
import Loader from './Loader.vue';

// dichiaro i componenti importati
export default {
  components: {
    Album,
    Loader,
  },
  // nei data inserisco:
  // - axios per la chiamata Api,
  // - un array vuoto dove salvo i dati dell'endpoint
  // - la variabile loading per la visualizzazione del caricamento
  data() {
    return {
      axios,
      albums: [],
      loading: true,
    };
  },
  created() {
    // chiamata API
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((res) => {
        this.albums = res.data.response;
        // una volta caricati i dati loading diventa false altrimenti verrebbe visualizzato senza soluzione di continuità
        this.loading = false
        console.log(this.albums);
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>

<style lang="scss" scoped>
</style>