<script setup lang="ts">

import * as paper from "paper";

const props = defineProps({
  element: {
    type: HTMLElement,
  }
})

function random(min: number, max: number) {
  return Math.random() * (max - min) + min;
}

const minRadius = 15
const maxRadius = 50
const maxSize = maxRadius ** 2
const baseSpeed = 0.25
const baseRotation = 0.10

class Star {
  point: paper.Point | undefined
  path: paper.Path | undefined

  radius2 = random(minRadius, maxRadius)
  radius1 = this.radius2 / 2

  sizeRatio = 1 - ((this.radius1 * this.radius2) / maxSize)
  moveSpeed = this.sizeRatio * baseSpeed
  rotSpeed = this.sizeRatio * baseRotation

  constructor() {

    if(props.element){
      const x = random(0, props.element?.offsetWidth)
      const y = -this.radius2
      this.point = new paper.Point(x, y)
      this.path = new paper.Path.Star(this.point, 5, this.radius1, this.radius2)
      this.path.fillColor = new paper.Color(0, 1, 0)
      this.path.rotation = random(0, 360)
    }
  }

  fall(){
    if(this.path){
      this.path?.rotate(this.rotSpeed)
      this.path?.position.y += this.moveSpeed
    }
  }

}

</script>

<template>
  <div>
    <img :src="getImageUrl()" :alt="getAlt()">
  </div>
</template>