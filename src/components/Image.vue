<script setup lang="ts">

const props = defineProps<{
  filename: string,
  dir: string,
  top?: string,
  left?: string,
  right?: string,
  bottom?: string,
  width?: string,
  height?: string,
  position?: string,
  alt?: string,
}>()

const position = props.position ? props.position : "relative"


function getAlt(){
  if(props.alt == undefined){
    const name = props.filename
    return name.substring(0, name.indexOf("."))
  }

  return props.alt
}

function getPath(){
    return props.dir + props.filename
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
  <img class="image" :src="getPath()" :alt="getAlt()">
</template>