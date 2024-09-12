<script setup>
import { ref } from 'vue'

const counter = ref(0)
const incrementCounter = () => {
  counter.value++
}

const boxColor = ref('pink')
const changeColor = () => {
  const colors = ['pink', 'lightcoral', 'lightpink', 'hotpink', 'palevioletred']
  boxColor.value = colors[Math.floor(Math.random() * colors.length)]
}

const images = [
  'https://i.pinimg.com/564x/9c/1e/d9/9c1ed9619bd2fef8ec83008f45d7d666.jpg',
  'https://i.pinimg.com/564x/39/c3/f1/39c3f14b8c652cc071910c546e2e92f2.jpg',
  'https://i.pinimg.com/564x/c5/93/c0/c593c0cb0e6aaa8f247f6e8d4a91d5dd.jpg',
  'https://i.pinimg.com/736x/89/83/95/8983952e4af885cdb2966dfa9d4bb5a3.jpg'
]
const currentImageIndex = ref(0)
const nextImage = () => {
  currentImageIndex.value = (currentImageIndex.value + 1) % images.length
}
const prevImage = () => {
  currentImageIndex.value =
    (currentImageIndex.value - 1 + images.length) % images.length
}
</script>

<template>
  <div class="container">
    <main>
      <h1 class="title">Flowers</h1>

      <section class="counter-section">
        <h2>Click Counter</h2>
        <p>Count: {{ counter }}</p>
        <button @click="incrementCounter">Increment Counter</button>
      </section>

      <section class="color-section">
        <h2>Box Color Changer</h2>
        <div :style="{ backgroundColor: boxColor, width: '250px', height: '250px' }"></div>
        <button @click="changeColor">Change Color</button>
      </section>

      <section class="carousel-section">
        <h2>Image Carousel</h2>
        <img :src="images[currentImageIndex]" alt="Carousel image" width="500" />
        <div class="carousel-controls">
          <button @click="prevImage">Previous</button>
          <button @click="nextImage">Next</button>
        </div>
      </section>
    </main>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Pinyon+Script&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html, body {
  height: 100%;
  margin: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: 'Poppins', sans-serif;
  background-image: url('https://i.pinimg.com/564x/78/2f/9a/782f9a6143b92b020bb2cd8709098688.jpg');
  background-size: cover;
  background-position: center;
}

body {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
}

.container {
  text-align: center;
  max-width: 900px;
  width: 100%;
  padding: 3rem 1.5rem;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  background-color: white;
  border-radius: 12px;
  box-sizing: border-box;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  min-height: 100vh;
}

main {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

h1.title {
  font-family: 'Pinyon Script', cursive;
  font-size: 4rem;
  color: #d81b60;
  margin-bottom: 1.5rem;
}


.counter-section,
.color-section,
.carousel-section {
  margin: 2.5rem 0;
  width: 100%;
  max-width: 750px;
}

h2 {
  color: #d81b60;
  margin-bottom: 1rem;
  font-size: 2rem;
}

p {
  font-size: 1.5rem;
  color: #333;
}

button {
  margin-top: 1.5rem;
  padding: 1rem 3rem;
  background-color: #ec407a;
  border: none;
  color: white;
  cursor: pointer;
  font-size: 1.2rem;
  border-radius: 8px;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #d81b60;
}

.color-section div {
  margin: 1.5rem auto;
  border: 3px solid #ec407a;
  border-radius: 8px;
}

.carousel-section img {
  display: block;
  margin: 1.5rem auto;
  border: 3px solid #ec407a;
  border-radius: 8px;
}

.carousel-controls {
  display: flex;
  justify-content: center;
  gap: 1rem;
}

.carousel-controls button {
  padding: 1rem 2rem;
}
</style>
