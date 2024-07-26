<script setup>
// slider libs
import { Carousel, Navigation, Pagination, Slide } from 'vue3-carousel'
import 'vue3-carousel/dist/carousel.css'
// slider libs


import slides from '../mocks/slides.js'
import { animate } from "motion"
import { ref } from 'vue'
 
let textIsShown = ref(true)

function hideText () {
  textIsShown.value = false
}

function showText () {
  textIsShown.value = true
}

</script>


<template>
  <Carousel class="sldr" 
    :transition="1000" :wrap-around="true"
    :autoplay="5000"
    @slide-start="hideText"
    @slide-end="showText"
  >
    <Slide v-for="slide in slides" :key="slide">
      <div class="sldr__item">
        <img class="sldr__img" :src="slide.img">
        <div class="sldr__cover" :style="slide.cover"></div>

        <transition name="fadeText">
          <h3 v-show="textIsShown" class="sldr__title">{{ slide.title }}</h3>
        </transition>

        <transition name="fadeText">
          <p v-show="textIsShown" class="sldr__desc">{{ slide.desc }}</p>
        </transition>

        <transition name="fadeText">
          <div v-show="textIsShown" class="sldr__bittons">
            <a href="#" class="sldr__button">Подбробнее</a>
            <a href="#" class="sldr__button sldr__button_white">В корзину</a>
          </div>
        </transition>
      </div>
    </Slide>

    <template #addons>
      <Navigation />
    </template>
  </Carousel>
</template>


<style>

.sldr {
  margin-top: -16px;
}

.sldr__item {
  width: 100%;
  height: 80vh;

  display: flex;
  justify-content: center;
  align-items: flex-start;
  flex-direction: column;
  gap: 40px;


  position: relative;
  color: white;

  padding: 10%;
}

.sldr__img {
  position: absolute;
  top: 0; left: 0;
  width: 100%; height: 100%;
  object-fit: COVER;
  object-position: bottom;
  filter: brightness(.8);
}

.sldr__cover {
  position: absolute;
  top: 0; left: 0;
  width: 100%; height: 100%;
}

.sldr__title {
  position: relative;
  margin: 0; padding: 0;
  font-size: 32px;
  font-weight: 500;
  transition: .5s;
}

.sldr__desc {
  position: relative;
  text-align: left;
  max-width: 50%;
  line-height: 30px;
  margin: 0; padding: 0;
  font-weight: 300;
  transition: .5s;
  transition-delay: .1s;
}

.sldr__bittons {
  position: relative;
  display: flex;
  gap: 30px;
  transition: .5s;
  transition-delay: .2s;
}

.sldr__button {
  padding: 10px 40px;
  background: none;
  color: inherit;
  text-decoration: none;
  font-weight: 200;

  border: 1px solid white;
  border-radius: 10px;
  outline: none;
  transition: .3s;
}

.sldr__button_white {
  background: white;
  color: black;
}

.sldr__button:hover {
  background: white;
  color: black;
}

.sldr__button_white:hover {
  padding: 10px 50px;
  font-weight: 400;
}


.carousel__prev,
.carousel__next {
  /* box-sizing: content-box; */
  color: white;
  opacity: .7;
}

.fadeText-leave-active {
  opacity: 0;
  transition: .2s;
}

.fadeText-enter-active {
  opacity: 0;
  transform: translateY(50px);
}

</style>