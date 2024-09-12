<template>
  <div @click="incrementCounter" class="app-container">
    <!-- Title -->
    <h1>Azizah Istiqomah</h1>
    
    <!-- Click Counter -->
    <h1>Click Counter</h1>
    <p>Total Clicks: {{ counter }}</p>
    <button @click.stop="undoCounter" :disabled="counter === 0">Undo</button> <!-- Undo button -->

    <!-- Box Color Changer -->
    <h1>Box Color Changer</h1>
    <div :style="{ backgroundColor: boxColor }" class="color-box"></div>
    <button @click="changeColor">Change Box Color</button>

    <!-- Image Carousel -->
    <h1>Image Carousel</h1>
    <div class="carousel">
      <img :src="images[currentImageIndex]" alt="carousel image" class="carousel-image">
    </div>
    <button @click="prevImage">Prev</button>
    <button @click="nextImage">Next</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      counter: 0, // For click counter
      boxColor: "#FF0000", // Initial color for the box
      currentImageIndex: 0, // Current image in carousel
      images: [
        "https://i.pinimg.com/564x/ff/d4/e9/ffd4e9f77290dacf52c016d782438ce2.jpg",
        "https://i.pinimg.com/736x/a6/bc/fc/a6bcfcea57b52aaf55d78db9d458483b.jpg",
        "https://i.pinimg.com/564x/8c/c6/8c/8cc68c702c85e005b7cd95c8ea16c505.jpg"
      ] // List of images for the carousel
    };
  },
  methods: {
    incrementCounter() {
      this.counter++;
    },
    undoCounter(event) {
      event.stopPropagation(); // Prevent triggering incrementCounter when clicking undo
      if (this.counter > 0) {
        this.counter--;
      }
    },
    changeColor() {
      // Change the color randomly
      const randomColor = "#" + Math.floor(Math.random() * 16777215).toString(16);
      this.boxColor = randomColor;
    },
    nextImage() {
      this.currentImageIndex = (this.currentImageIndex + 1) % this.images.length;
    },
    prevImage() {
      this.currentImageIndex = (this.currentImageIndex - 1 + this.images.length) % this.images.length;
    }
  }
};
</script>

<style scoped>
.app-container {
  text-align: center;
  padding: 20px;
}

.color-box {
  width: 200px;
  height: 200px;
  margin: 20px auto;
}

.carousel {
  margin: 20px auto;
}

.carousel-image {
  width: 300px;
  height: 300px;
}
</style>
