<template>
  <div>
    <v-container class="bg" height="640" width="1200">
      <v-row>
        <v-col cols="12">
          <h1 id="title-word" class="text-center">What do you want explore?</h1>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="12" style="margin: auto; position: relative">
          <a
            v-for="(card, idx) in cards"
            :key="idx"
            ref="hoverBlock"
            class="block hover-z"
            height="366"
          >
            <v-img class="hover" cover height="100%" :src="card.image" />
            <div class="overlay-text">
              <h4>{{ card.caption }}</h4>
            </div>
          </a>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script setup>
import { gsap } from 'gsap'
import { ref } from 'vue'

const hoverBlock = ref(null)

const cards = [
  {
    image: new URL('@/assets/images/paintings/1.jpg', import.meta.url).href,
    caption: 'City View',
  },
  {
    image: new URL('@/assets/images/paintings/2.jpg', import.meta.url).href,
    caption: 'Beach House',
  },
  {
    image: new URL('@/assets/images/paintings/3.jpg', import.meta.url).href,
    caption: 'Castle',
  },
  {
    image: new URL('@/assets/images/paintings/4.jpg', import.meta.url).href,
    caption: 'Alpine Retreat',
  },
]

function onMouseMove(e) {
  const el = hoverBlock.value
  const rect = el.getBoundingClientRect()

  const offsetX = e.clientX - rect.left
  const offsetY = e.clientY - rect.top
  const centerX = rect.width / 2
  const centerY = rect.height / 2

  // 計算相對中心的距離比例（-1 ~ 1）
  const moveX = ((offsetX - centerX) / centerX) * 20
  const moveY = ((offsetY - centerY) / centerY) * 20

  gsap.to(el, {
    scale: 1.2,
    x: moveX,
    y: moveY,
    duration: 0.3,
    ease: 'power2.out',
  })
}

function onMouseLeave() {
  const el = hoverBlock.value
  gsap.to(el, {
    scale: 1,
    x: 0,
    y: 0,
    duration: 0.5,
    ease: 'power2.out',
  })
}
</script>

<style scoped>
.bg {
  width: 1905px;
  height: 610px;
  font-family: 'Google Sans', 'Noto Naskh Arabic UI', Arial, sans-serif;
}

#title-word {
  letter-spacing: 0;
  font-weight: 400;
  line-height: 2.75rem;
  font-size: 2.25rem;
}

.block {
  color: white;
  font-size: 100px;
  text-align: center;
  width: 400px;
  height: 400px;
  border-radius: 10px;
  position: absolute;
  overflow: hidden;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
}

.block:first-of-type {
  left: 0;
}

.block:nth-of-type(2) {
  left: 250px;
}

.block:nth-of-type(3) {
  left: 500px;
}

.block:nth-of-type(4) {
  left: 750px;
}

.overlay-text {
  position: absolute;
  bottom: 0;
  color: white;
  background: linear-gradient(to top, rgba(0, 0, 0, 0.6), transparent);
  width: 100%;
  padding: 12px;
  font-size: 22px;
}

.hover {
  transition: transform 0.5s ease;
  cursor: pointer;
}

.hover:hover {
  transform: scale(1.1);
}

h4 {
  font-size: 22px;
  text-align: left;
}

.hover-z:hover {
  z-index: 1;
}
</style>
