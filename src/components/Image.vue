<script setup lang="ts">

const props = defineProps({
  filename: {
    type: String,
    required: true
  },
  top: String,
  left: String,
  right: String,
  bottom: String,
  alt: String,
})


function getAlt(){
  if(props.alt === undefined){
    const name = props.filename
    return name.substring(0, name.indexOf("."))
  }

  return props.alt
}

function getImageUrl() {
  try {
    return new URL(`../assets/${props.filename}`, import.meta.url).toString()
  } catch (e) {
    console.log((e as Error).message);
  }
}

</script>

<style scoped>
.image {
  position: absolute;
  top: v-bind(top);
  bottom: v-bind(bottom);
  left: v-bind(left);
  right: v-bind(right);
}
</style>

<template>
  <div>
    <img class="image" :src="getImageUrl()" :alt="getAlt()">
  </div>
</template>