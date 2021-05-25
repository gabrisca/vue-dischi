<template>
  <form class="d-flex mt-3 mb-3">
    <div class="flex-grow-1">
     <input v-model.trim='searchText' @keyup.enter='startSearch' class="form-control" type="text" placeholder="Find author"> 
    </div>
    <div class="ms-3">
      <!-- .prevent evita che si ricarichi la pagina ogni volta che clicco -->
      <button @click.prevent='startSearch' class="btn btn-primary"> 
        Cerca
      </button>
    </div>
    <div class="ms-3">
      <!-- .prevent evita che si ricarichi la pagina ogni volta che clicco -->
      <button @click.prevent='resetSearch' class="btn btn-warning"> 
        Reset
      </button>
    </div>
  </form>
</template>

<script>
export default {
  name: 'Search',
  data(){
    return {
      searchText: ''
    }
  },
  methods: {
    // funzione che fa partire la ricerca
    startSearch(){
      // $emit è un evento che viene letto dal padre
      this.$emit('searchAlbum', this.searchText)
      console.log(this.searchText);
    },
    // funzione che resetta la ricerca
    resetSearch(){
      this.searchText = '';
      this.startSearch();
    }
  },
}
</script>

<style lang='scss' scoped>
  input {
    &:focus {
      border-color: #3AD65E;
      box-shadow: inset 0 1px 1px #3ad65e5e, 0 0 4px #3AD65E;
    }
  }
</style>