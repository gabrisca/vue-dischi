<template>
  <div
    class="wrap d-flex justify-content-center align-items-center flex-column"
  >
    <h3>{{ title }}</h3>
    <div class="lds-ripple">
      <div></div>
      <div></div>
    </div>
    <h4>Loading</h4>
  </div>
</template>

<script>
export default {
  // preparo Loader per essere esportato
  name: "Loader",
  // props per cambiare il titolo all'occorrenza
  props: {
    title: String,
  },
};
</script>

<style lang="scss" scoped>
.wrap {
  height: 80vh;
}
.lds-ripple {
  display: inline-block;
  position: relative;
  width: 80px;
  height: 80px;
}
.lds-ripple div {
  position: absolute;
  border: 4px solid #3AD65E;
  opacity: 1;
  border-radius: 50%;
  animation: lds-ripple 1.3s cubic-bezier(0, 0.2, 0.8, 1) infinite;
}
.lds-ripple div:nth-child(2) {
  animation-delay: -0.8s;
}
@keyframes lds-ripple {
  0% {
    top: 36px;
    left: 36px;
    width: 0;
    height: 0;
    opacity: 1;
  }
  100% {
    top: 0px;
    left: 0px;
    width: 72px;
    height: 72px;
    opacity: 0;
  }
}
</style>