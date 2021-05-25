<template>
  <div class="container mt-5 text-center">
    <!-- salvo in un div con condizione !loading il mio contenuto -->
    <div 
    v-if="!loading"
    class="row d-flex justify-content-center">
      <Search 
      @searchAlbum='searching'
      />
      <Album 
      v-for="(album, index) in filteredAlbums" 
      :key="index" 
      :album="album"
       />
       <div class="text-center mt-3">
         <h6>Album trovati: {{ filteredAlbums.length }}</h6>
       </div>
       <SelectGenre />
    </div>
    <!-- se loading è true mostro Loader con icona caricamento pagina -->
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
// importo Search
import Search from './Search.vue';
// importo SelectGenre
import SelectGenre from './SelectGenre.vue';

// dichiaro i componenti importati
export default {
  components: {
    Album,
    Loader,
    Search,
    SelectGenre,
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
      // variabile textToSearch che accoglie il testo inviato dal figlio (di default è vuota)
      textToSearch:'',
    }
  },
  computed: {
    // filtro gli album in base al titolo
    filteredAlbums(){
      return this.albums.filter(item => item.author.toLowerCase().includes(this.textToSearch.toLowerCase()))
    }
  },
  methods: {
    // funzione richiamata da evento custom che riceve come parametro il testo da cercare
    searching(text){
      this.textToSearch = text;
      console.log(text);
    }
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