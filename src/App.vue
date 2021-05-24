<template>
  <div id="app">
      <Header />
      <Main />
  </div>
</template>

<script>
// importo Header e Main
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: "App",
  // dichiaro i componenti importati
  components: {
    Header,
    Main,
  },
};
</script>

<style lang="scss">
// importo il foglio di stile general.scss
@import "@/assets/style/general";
</style>
