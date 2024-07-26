<script setup>
import { onMounted } from 'vue';
import {animate, stagger, timeline} from "motion"


onMounted(() => {
  let sequence = [
    [
      '.cHead__cover',
      { opacity: [0, 1], translateY: [-50, 0] },
      { duration: .7}
    ],
    "titleAnim",
    [
      '.cHead__decor',
      { opacity: [0, 1]},
      { duration: 2, at: 'titleAnim' }
    ],
    [
      '.cHead__decor_top',
      { translateX: [-150, 0] }, 
      { duration: 1, at: 'titleAnim' }
    ],
    [
      '.cHead__decor_bot',
      { translateX: [150, 0] }, 
      { duration: 1, at: 'titleAnim' }
    ],
    [
      '.cHead__titleText',
      { opacity: [0, 1]},
      { duration: 1, at: 'titleAnim' }
    ],
    [
      '.card',
      { opacity: [0, 1], },
      { 
        duration: 2, delay: stagger(0.1) ,
        at: 'titleAnim'
      }
    ],
  ]

  timeline(sequence)
})

</script>

<template>
  <div class="cHead">
    <img class="cHead__cover"
      src="/img/products/atlant.jpg"
    >

    <div class="cHead__title">
      <img class="cHead__decor cHead__decor_top"
        src="/img/icons/decor-top.svg"
      >

      <h1 class="cHead__titleText">Тротуарная плитка</h1>

      <img class="cHead__decor cHead__decor_bot"
        src="/img/icons/decor-bottom.svg"
      >
    </div>
  </div>
</template>


<style>
.cHead {
  display: flex;
  justify-content: center;
  align-items: center;

  position: relative;
  height: 35vh;
}

.cHead__cover {
  position: absolute;
  height: 100%; width: 100%;

  object-fit: cover;
  object-position: center;

  border-radius: 0 0 40px 40px;
  filter: brightness(.8);

}

.cHead__title {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
}


.cHead__title {
  margin: 0; padding: 0 50px;
  color: white;
  text-align: center;
}

.cHead__titleText {
  margin: 10px 100px;
}

.cHead__decor {
  position: absolute;
}

.cHead__decor_top {
  top: -40px; left: 0;
}

.cHead__decor_bot {
  right: 0; bottom: -40px;
}

</style>