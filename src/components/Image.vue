<script setup lang="ts">

const props = defineProps<{
  path: string,
  width?: string,
  height?: string,
  alt?: string,
}>()

function getAlt() {
  if (props.alt == undefined) {
    const path = props.path
    return path.substring(path.lastIndexOf('/'), path.indexOf("."))
  }

  return props.alt
}

</script>

<style scoped>
.image {
  width: v-bind(width);
  height: v-bind(height);
}
</style>

<template>
  <img class="image" :src="props.path" :alt="getAlt()">
</template>