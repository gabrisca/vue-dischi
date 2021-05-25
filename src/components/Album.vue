<template>
  <div id="album" class="col-sm-6 col-md-3 col-lg-2 m-3">
    <img :src="album.poster" class="img-fluid" :alt="album.title" />
    <h3 class="d-flex justify-content-center">{{ album.title }}</h3>
    <h5>{{ album.author }}</h5>
    <h5>{{ album.year }}</h5>
  </div>
</template>

<script>
export default {
  name: "Album",
  props: {
    album: Object,
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/style/general";
#album {
  background-color: $color-header;
  transition: all 0.8s;
  cursor: pointer;
  padding: 30px;
  min-height: 360px;
  &:hover {
    transform: scale(1.1);
    filter: brightness(1.1);
  }
  img {
    margin-bottom: 20px;
    height: 170px;
  }
  h3 {
    text-transform: uppercase;
    font-size: 1.2em;
    font-weight: bolder;
    margin-bottom: 30px;
  }
  h5 {
    color: #797471;
    font-size: 0.9em;
  }
}
</style>