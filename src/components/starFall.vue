<script setup lang="ts">

import paper from "paper";

function random(min: number, max: number) {
  return Math.random() * (max - min) + min;
}

const minRadius = 15
const maxRadius = 50
const maxSize = maxRadius ** 2
const baseSpeed = 2
const baseRotation = 0.5

const starArr: Star[] = []

class Star {
  point: paper.Point
  path: paper.Path

  radius2 = random(minRadius, maxRadius)
  radius1 = this.radius2 / 2
  done = false

  sizeRatio = 1 - ((this.radius1 * this.radius2) / maxSize)
  moveSpeed = this.sizeRatio * baseSpeed
  rotSpeed = this.sizeRatio * baseRotation

  constructor() {
    this.point = new paper.Point({
      x: random(0, paper.view.viewSize.width),
      y: random(0, paper.view.viewSize.height * 0.75)
    })

    this.path = new paper.Path.Star(this.point, 5, this.radius1, this.radius2)
    this.path.fillColor = new paper.Color(0, 1, 0, 0)
    this.path.rotation = random(0, 360)
    this.path.shadowColor = this.path.fillColor
    this.path.shadowBlur = ((this.radius1 * this.radius2) / maxSize) * 50
  }

  fall() {
    if (this.path.fillColor!.alpha < 1)
      this.path.fillColor!.alpha += 0.01

    if (this.path.position.y < paper.view.size.height + this.radius2) {
      this.path.rotate(this.rotSpeed)
      this.path.position.y += this.moveSpeed
    } else {
      this.path.remove()
      const index = starArr.indexOf(this)
      starArr.slice(index, 1)
      this.regen()
    }
  }

  regen() {
    if (!this.done)
      starArr.push(new Star())

    this.done = true
  }

}

const canvas =  document.getElementById("canvas") as HTMLCanvasElement

let overlay: HTMLDivElement | undefined

paper.setup(canvas)
const numWanted = 75

for (let i = 0; i < numWanted; i++) {
  const star = new Star()
  starArr.push(star)
}

paper.view.onFrame = function () {
  for (const star of starArr) {
    star.fall()
  }
}

paper.view.onResize = function () {
  canvas.width = window.innerWidth
  canvas.height = window.innerHeight
}

</script>

<style scoped>

#canvas[onresize] {
  width: inherit;
  height: inherit;
  z-index: -50;

  position: absolute;
  display: block;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

</style>

<template>
  <canvas id="canvas"></canvas>


</template>