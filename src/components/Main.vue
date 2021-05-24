<template>
  <div class="container mt-5 text-center">
    <div 
    v-if="!loading"
    class="row d-flex justify-content-center">
      <Album 
      v-for="(album, index) in albums" 
      :key="index" 
      :album="album"
       />
    </div>
      <Loader 
      v-else
      title="Spotify"
      />
  </div>
</template>

<script>
import Album from "./Album.vue";
import axios from "axios";
import Loader from './Loader.vue';

export default {
  components: {
    Album,
    Loader,
  },
  data() {
    return {
      axios,
      albums: [],
      loading: true,
    };
  },
  created() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((res) => {
        this.albums = res.data.response;
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