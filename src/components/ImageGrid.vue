<template>
  <div id="imageGrid">
    <img v-for="(image, index) in images" :key="index" :src="getPath(image)" :alt="getAlt(image)"
         :style="getImageStyle(index)">
  </div>
</template>

<style scoped>

#imageGrid {
  display: grid;
  grid-template-columns: repeat(3, 1fr); /* 3 columns */
  grid-auto-rows: auto; /* Auto size rows */
  grid-auto-flow: dense;
  gap: 10px;
  justify-items: center;
  padding: 20px;
}

#imageGrid img {
  max-width: 50%; /* Set maximum width to fill grid cell */
  max-height: fit-content; /* Allow assets to scale proportionally */
}
</style>

<script setup lang="ts">

const rows = 3
const columns = 4

const props = defineProps<{
  images: string[];
  dir: string;
}>();

function getPath(name: string){
  return props.dir + name
}

function getAlt(name: string) {
  return name.substring(0, name.indexOf("."))
}

function getImageStyle(index: number) {
  const column = index % rows; // 3 assets per row
  const row = Math.floor(index / columns); // Calculate row based on 3 assets per row

  return {
    gridColumn: `${column + 1} / span ${column}`, // Set grid column and span
    gridRow: `${row + 1} / span ${row}` // Set grid row and span
  };
}

</script>

