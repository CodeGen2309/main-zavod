<script setup>
import sliderVue from "./components/slider.vue";
import productCard from "./components/productCard.vue";

import '../public/fonts/stylesheet.css'



</script>


<template>
  <div class="tstHolder">
    <productCard></productCard>
  </div>
</template>


<style>
body {
  margin: 0; padding: 0;
  font-family: 'roboto';
}

.tstHolder {
  width: 100%; height: 100vh;

  display: flex;
  justify-items: center;
  align-items: center;
}
</style>