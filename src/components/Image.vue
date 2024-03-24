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
  width: String,
  height: String,
  position: String,
  alt: String,
})

const position = props.position ? props.position : "relative"


function getAlt(){
  if(props.alt === undefined){
    const name = props.filename
    return name.substring(0, name.indexOf("."))
  }

  return props.alt
}

</script>

<style scoped>
.image {
  position: v-bind(position);
  top: v-bind(top);
  bottom: v-bind(bottom);
  left: v-bind(left);
  right: v-bind(right);

  width: v-bind(width);
  height: v-bind(height);
}
</style>

<template>
  <img class="image" :src="props.filename" :alt="getAlt()">
</template>