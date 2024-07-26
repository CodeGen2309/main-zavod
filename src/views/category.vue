<script setup>
import { onMounted } from "vue";
import { animate, stagger } from "motion"

import productCard from "../components/productCard.vue";
import products from "../mocks/products";
import catHeader from "@/components/catHeader.vue";
import tabs from "@/components/tabs.vue";

let tabData = [
  {title: 'хиты продаж' },
  {title: 'цена со скидкой' },
  {title: 'премиум' },
  {title: 'сначала популярное' },
  {title: 'полный окрас' },
  {title: 'декоративное покрытие' },
  {title: 'показать все фильтры' },
  {title: 'цена со скидкой' },
  {title: 'премиум' },
  {title: 'сначала популярное' },
  {title: 'полный окрас' },
  {title: 'декоративное покрытие' },
]


onMounted(() => {
  animate(
    '.tab',
    { opacity: [0, 1], translateX: [-100, 0] },
    { duration: 1, delay: stagger(0.1) }
  )
})

</script>

<template>
<catHeader></catHeader>

<tabs class="tst__tabs" 
  :images="false" :tab-data="tabData"
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


<style scopded>
.tst__tabs {
  margin: 60px 200px;
}

.tab {
  height: 40px;
}

.tab:hover {
  color: white;
  background: rgba(41, 128, 185,1.0);
}

.tst__holder {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: 250px;
  grid-auto-flow: dense;
  gap: 30px;

  margin: 60px 150px;
  box-sizing: border-box;
}

</style>