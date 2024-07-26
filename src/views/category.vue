<script setup>
import { onMounted } from "vue";
import { animate } from "motion"

import productCard from "../components/productCard.vue";
import products from "../mocks/products";
import catHeader from "@/components/catHeader.vue";
import tabs from "@/components/tabs.vue";


onMounted(() => {
  animate(
    '.tst__tabs',
    { opacity: [0, 1], translateY: [-100, 0] },
    { duration: 1, delay: 0.5 }
  )
})

</script>

<template>
<catHeader></catHeader>

<tabs class="tst__tabs" 
  :images="false"
/>

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
.tst__holder {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: 230px;
  grid-auto-flow: dense;
  gap: 30px;

  margin: 60px;
  box-sizing: border-box;
}

</style>