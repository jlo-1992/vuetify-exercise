<template>
  <div style="background: #e05e4e">
    <v-container height="640" width="1200">
      <v-row>
        <v-col class="text" cols="12">
          <h1>Get your 5 a day</h1>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="12">
          <h5 class="text">Art so delicious you can practically taste it</h5>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="12">
          <div v-for="(img, idx) in imgs" :key="idx" class="block">
            <v-img contain :src="img" />
          </div>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script setup>
const imgs = [
  new URL('@/assets/images/fruits/1.jpg', import.meta.url).href,
  new URL('@/assets/images/fruits/2.jpg', import.meta.url).href,
  new URL('@/assets/images/fruits/3.jpg', import.meta.url).href,
  new URL('@/assets/images/fruits/4.jpg', import.meta.url).href,
  new URL('@/assets/images/fruits/5.jpg', import.meta.url).href,
]
</script>

<style scoped>
.block {
  width: 198px;
  height: 454px;
  border: 1px solid black;
  border-radius: 20px;
  transition: 0.5s;
  display: inline-block;
}

.block:hover {
  transform: scaleX(1.7);
}

.block v-img {
  border-radius: 20px;
}
.block v-img:hover {
  transform: scale(1.2);
}

.text {
  color: white;
  text-align: center;
}
</style>
