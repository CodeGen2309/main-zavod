<script setup>
import { defineProps, ref, onMounted } from 'vue';
import { animate, inView, stagger } from "motion"

// slider libs
import { Carousel, Navigation, Pagination, Slide } from 'vue3-carousel'
import 'vue3-carousel/dist/carousel.css'
// slider libs



let props = defineProps([
  'cover', 'title',  'desc',
  'price', 'labels', 'attrs',
  'gallery', 'link', 'cardSize'
])

let isWide = props.cardSize == 'wide'
let isLarge = props.cardSize == 'large'
let sliderEpt = ref(null)

let classes = {
  'holder': {
    'card__holder': true,
    'card__holder_wide': isWide,
    'card__holder_large': isLarge
  },

  'card': {
    'card': true,
    'card_wide': isWide,
    'card_large': isLarge,
    'card_min': !isWide && !isLarge
  },

  'cover': {
    'card__cover': true,
    'card__cover_wide': isWide,
    'card__cover_large': isLarge,
  },

  'content': {
    'card__content': true,
    'card__content_wide': isWide,
    'card__content_large': isLarge,

  },

  'title': {
    'card__title': true,
    'card__title_wide': isWide,
    'card__title_large': isLarge,
  },

  'desc': {
    'card__desc': true,
    'card__desc_wide': isWide,
    'card__desc_large': isLarge,
  },

  'price': {
    'card__price': true,
    'card__price_wide': isWide,
    'card__price_large': isLarge
  },

  'button': {

  },

}

function fadeView () {
  inView( '.card', 
    info => {
      animate(info.target, 
        { opacity: [0, 1] }, 
        { duration: 1 }
      )
    },
    { margin: '0px 0px -70px 0px' }
  )
}


// onMounted(() => { fadeView() })
</script>



<template>
<div  :class="classes.holder" >
  <div :class="classes.card" >
    <div :class="classes.cover">
      <img v-if="!isLarge || isWide"
        class="card__img" :src="cover"
      >

      <Carousel v-if="isLarge"
        ref="sliderEpt"
        class="card__slider"
        :autoplay="3000" :wrap-around="true"
        :transition="600"
      >

      <Slide v-for="slide in gallery" :key="slide"
        class="card__slide"
      >
        <div class="card__slideInner">
          <img class="card__slideImg" :src="slide" alt="">
        </div>
      </Slide>

      </Carousel>

      <p :class="classes.price" >
        {{ price }}
        <img src="/img/icons/rouble.svg" alt="">
      </p>
    </div>

    <div :class="classes.content" >
    <div class="card__gallery" v-if="isLarge">
      <img v-for="(item, id) in gallery"  :key="item"
        :src="item" class="card__galleryImg"
        @click="sliderEpt.slideTo(id)" :alt="id"
      >
    </div>

      <h3 :class="classes.title">{{ title }}</h3>
      <p :class="classes.desc" v-if="isWide || isLarge">
        {{ desc }}
      </p>

      <a v-if="isWide || isLarge"
        class="card__buy card__buy_inner"
        href="#"
      >
        <img class="card__buyIcon" src="/img/icons/cart.svg" alt="">
        <span class="card__buyText">в корзину</span>
      </a>
    </div>
  </div>

  <a v-if="!isWide && !isLarge"
    class="card__buy card__buy_outer" 
    href="#"
  >
    <img class="card__buyIcon" src="/img/icons/cart.svg" alt="">
    <span class="card__buyText">в корзину</span>
  </a>
</div>
</template>


<style>
.card__holder {
  position: relative;
  transition: .3s;
}

.card__holder:hover .card_min {
  transform: translateY(-20px);
}

.card__holder_wide {
  grid-column: span 2;
}

.card__holder_large {
  /* grid-column: span 2; */
  grid-row: span 2;
}

.card__holder:hover .card__buy_outer {
  opacity: 1;
  z-index: 99;
  transform: translateX(-20px);
}

.card {
  display: flex;
  flex-direction: column;
  width: 100%; height: 100%;

  position: relative;
  overflow: hidden;
  border: 1px solid rgba(0, 0, 0, .2);
  border-radius: 10px;
  /* opacity: 0; */

  box-shadow: 1px 1px 10px 1px rgba(0, 0, 0, .3);
  transition: .3s;
}

.card_wide {
  flex-direction: row;
}

.card_large {
  box-sizing: border-box;
}

.card__cover {
  position: relative;
  display: flex;
  align-items: flex-end;
  flex-grow: 1;
  overflow: hidden;
}

.card__cover_wide {
  max-width: 50%;
}


.card__cover_large {
  display: flex;
  justify-content: stretch;
  align-items: stretch;
}

.card__slider {
  width: 100%; height: 300px;
}


.card__slide {
  min-height: 350px;
  margin-top: -20px;
}

.card__slideInner {
  position: relative;
  height: 100%; width: 100%;
}

.card__slideImg {
  position: absolute;
  top: 0; left: 0;
  right: 0; bottom: 0;
  width: 100%; height: 100%;

  object-fit: cover;
  object-position: bottom;
}


.card__img {
  width: 100%; height: 100%;

  object-fit: cover;
  object-position: center;
  filter: brightness(.9);
}

.card__price {
  border-radius: 0 10px 0 0;
  background: white;
  position: absolute;
  margin: 0; padding: 10px 20px;
  align-self: flex-end;
  font-weight: 300;
}

.card__price_wide {
  right: 0;
  border-radius: 6px 0 0 0;
}

.card__gallery {
  display: flex;
  height: 50px;
  gap: 4px;
}

.card__galleryImg {
  height: 100%;
  flex-grow: 1;
  overflow: hidden;
  border-radius: 6px;

  object-fit: cover;
  object-position: center;
}


.card__content{
  display: flex;
}

.card__content_wide {
  display: flex;
  flex-direction: column;
  gap: 20px;


  width: 50%;
  padding: 20px;
  box-sizing: border-box;
}

.card__content_large {
  display: flex;
  flex-direction: column;
  gap: 20px;
  padding: 20px;
}

.card__desc{
  margin: 0; padding: 0;
  font-weight: 200;
  color: rgba(0, 0, 0, .8);
}

.card__desc_wide {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: normal;
  font-size: 13px;
  flex-grow: 1;
}

.card__desc_large {
  max-height: 40px;
  overflow: hidden;
}

.card__title {
  margin: 0; padding: 15px 20px;
  font-weight: 500;
  font-size: 18px;
}

.card__title_wide {
  margin: 0; padding: 0;
}

.card__title_large {
  margin: 0; padding: 0;
}

.card__buy {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 10px;

  color: white;
  background: rgba(41, 128, 185, 1);
  text-decoration: none;

  margin: 0;
  border-radius: 4px;

  font-size: 18px;
  font-weight: 200;
  transition: .3s;
}

.card__buy_inner {
  padding: 10px 0;
  /* margin: 0 -20px -20px -20px; */

}

.card__buy_inner:hover {
  background: rgba(41, 128, 185, .7);
}

.card__buy_outer {
  position: absolute;
  right: -50px; bottom: -20px;
  width: 200px; height: 50px;
  box-shadow: 0px 0px 10px 2px rgba(0, 0, 0, .3);
  opacity: 0;
  /* z-index: -1; */
}

.card__buyIcon {

}

.card__buyText {

}
</style>