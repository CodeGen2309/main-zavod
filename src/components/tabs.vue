<script setup>
import { defineProps } from 'vue';
import { RouterLink } from 'vue-router';

defineProps({
  images: {default: true},
  tabData: {
    default: [
      {title: 'Тротуарная <br> плитка', image: '/img/tabs/1.jpg'},
      {title: 'Детское <br> игровое', image: '/img/tabs/2.jpg'},
      {title: 'Рядовой <br> кирпич', image: '/img/tabs/3.jpg'},
      {title: 'Деревянные <br> окна', image: '/img/tabs/4.jpg'},
      {title: 'Плиты <br> перекрытия', image: '/img/tabs/5.jpg'},
      {title: 'Лицевой <br> кирпич', image: '/img/tabs/6.jpg'},
      {title: 'Бортовые <br> блоки', image: '/img/tabs/7.jpg'},
      {title: 'Керамзитовый <br> гравий', image: '/img/tabs/8.jpg'},
      {title: 'Спортивное <br> оборудование', image: '/img/tabs/9.jpg'},  
    ]
  }
})


</script>


<template>
  <div class="tabHolder">
    <hr class="tab__decor">
    <div class="tab__holder">
      <router-link to="/cat" v-for="tab in tabData"
        :key="tab.image" class="tab"
      >
        <img v-if="images" class="tab__image" :src="tab.image">
        <p v-html="tab.title" class="tab__title"></p>
      </router-link>
    </div>
    <hr class="tab__decor">
  </div>
</template>


<style>
.tab__decor {
  width: 60%;
  background: none;
  border: none;
  border-bottom: 1px solid rgba(0, 0, 0, .4);
  margin: 20px auto;
  box-sizing: border-box;
}

.tab__holder {
  display: flex;
  flex-wrap: wrap;
  box-sizing: border-box;
  justify-content: space-around;
}

.tab {
  display: flex;
  align-items: center;
  flex-grow: 1;
  text-decoration: none;
  color: inherit;

  height: 60px; margin: 10px;
  max-width: 300px;

  box-shadow: 0 0 5px 1px rgba(0, 0, 0, .4);
  border-radius: 10px;
  overflow: hidden;

  cursor: pointer;
  transition: .3s;
}

.tab:hover {
  transform: scale(1.03);
  box-shadow: 0 0 10px 3px rgba(0, 0, 0, .4);
}

.tab__image {
  height: 100%;
  width: 120px;
  object-fit: cover;
  object-position: center;
}

.tab__title {
  text-align: center;
  margin: 0 20px; padding: 0;
  justify-self: center;
  flex-grow: 1;
}
</style>