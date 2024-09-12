<template>
  <div id="app">
    <!-- Counter Section -->
    <div>
      <p>Count: {{ count }}</p>
      <button @click="increment">Increment</button>
    </div>

    <!-- Color Box Section -->
    <div>
      <p>Change Background Color:</p>
      <button @click="changeColor('red')">Red</button>
      <button @click="changeColor('green')">Green</button>
      <button @click="changeColor('blue')">Blue</button>
      <button @click="changeColor('yellow')">Yellow</button>
      <button @click="changeColor('white')">Kembali</button>
    </div>

    <!-- Color Box Display -->
    <div :style="{ backgroundColor: boxColor, width: '100px', height: '100px', margin: '20px auto' }"></div>

    <!-- Image Carousel Section -->
    <div>
      <p>Image Carousel:</p>
      <button @click="prevImage">Previous</button>
      <button @click="nextImage">Next</button>
      <div class="carousel">
        <img :src="images[currentImage]" alt="Carousel Image" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      count: 0,
      boxColor: 'white', // Default color for the box
      images: [
        'https://via.placeholder.com/400x300.png?text=Image+1',
        'https://via.placeholder.com/400x300.png?text=Image+2',
        'https://via.placeholder.com/400x300.png?text=Image+3'
      ],
      currentImage: 0
    };
  },
  methods: {
    increment() {
      this.count += 1;
    },
    changeColor(color) {
      this.boxColor = color;
    },
    nextImage() {
      this.currentImage = (this.currentImage + 1) % this.images.length;
    },
    prevImage() {
      this.currentImage = (this.currentImage - 1 + this.images.length) % this.images.length;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

button {
  font-size: 16px;
  padding: 10px;
  cursor: pointer;
  margin: 5px;
}

.carousel {
  margin: 20px auto;
  width: 400px; /* Adjust width as needed */
  height: 300px; /* Adjust height as needed */
}

.carousel img {
  width: 100%;
  height: auto;
  display: block;
}
</style>
