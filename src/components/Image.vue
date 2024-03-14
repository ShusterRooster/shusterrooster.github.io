<script setup lang="ts">

const props = defineProps({
  filename: {
    type: String,
    required: true
  },
  alt: String
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

<template>
  <div>
    <img :src="getImageUrl()" :alt="getAlt()">
  </div>
</template>