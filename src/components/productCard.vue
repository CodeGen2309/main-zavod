<script setup>
defineProps([
  'cover', 'title',  'desc',
  'price', 'labels', 'attrs',
  'size', 'gallery', 'link'
])



</script>



<template>
<div class="card">
  <img class="card__img" src="/img/slides/5.jpg">
  <p class="card__price">1943 р.</p>
  <h3 class="card__title">Ебейшая дрочь</h3>
</div>  
</template>


<style>
.card {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;

  position: relative;
  width: 300px;

  overflow: hidden;
  border-radius: 10px;

  margin: 40px;
  box-shadow: 0px 0px 10px 4px rgba(0, 0, 0, .4);
}

.card__img {
}

.card__price {
  overflow: hidden;
  border-radius: 0 10px 0 10px;
  margin-top: -40px;
  position: relative;
  background: white;
  margin: 0; padding: 10px;
  align-self: flex-start;
}

.card__title {

}

</style>