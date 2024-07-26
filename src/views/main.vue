<script setup>
import slider from "../components/slider.vue";
import tabs from "../components/tabs.vue";

import productCard from "../components/productCard.vue";
import products from "../mocks/products";

</script>


<template>
  <slider></slider>
  <tabs></tabs>

  <div class="tst__holder">
    <productCard class="tst_card"
      v-for="item in products" :key="item.title" 
      :cover="item.img" :price="item.price"
      :title="item.title" :card-size="item.cardSize"
      :desc="item.desc" :gallery="item.gallery"
    />
  </div>
</template>


<style>
body {
  margin: 0; padding: 0;
  font-family: 'roboto';
}

.tst__holder {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-auto-rows: 230px;
  grid-auto-flow: dense;
  gap: 30px;

  margin: 60px;
  box-sizing: border-box;
}

.tst_card {
  animation: fadeScroll 2s linear both;
  animation-timeline: view();
}

@media (width < 1000px) {
  .tst__holder {
    grid-template-columns: repeat(3, 1fr);
  }
}

@media (width > 1200px) {
  .tst__holder {
    grid-template-columns: repeat(5, 1fr);
  }
}

@keyframes fadeScroll {
  0% { 
    /* transform: scale(.9); */
    transform: translateY(100px);
    /* opacity: 0.4; */
  }
  30% { 
    transform: translateY(0);
    /* transform: scale(1); */
    /* opacity: 1;  */
  }

  /* 50% { transform: translateY(0); } */

  80% { 
    opacity: 1; 
  }
  100% { 
    opacity: 0; 
  }
}
</style>