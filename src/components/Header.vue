<template>
  <header>
    <div class="wrapper">
      <div class="logo">
        <img src="../assets/img/logo.png" alt="logo spotify">
      </div>
    </div>
  </header>
</template>

<script>
export default {
  // preparo Header per essere esportato
  name: 'Header'
}
</script>

<style lang="scss" scoped>
    /* // importo le variabili */
  @import '../assets/style/vars.scss';
  .wrapper {
    width: 100%;
    height: 60px;
    background-color: $color-header;
    .logo{
      width: 100px;
      height: 100%;
      padding: 5px;
      text-align: center;
      img {
        height: 90%;
        cursor: pointer;
        &:hover {
          filter: brightness(1.2);
        }
      }
    }
  }
</style>