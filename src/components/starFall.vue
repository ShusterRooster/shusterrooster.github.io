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
  element: HTMLElement
  point: paper.Point
  path: paper.Path

  radius2 = random(minRadius, maxRadius)
  radius1 = this.radius2 / 2
  done = false

  sizeRatio = 1 - ((this.radius1 * this.radius2) / maxSize)
  moveSpeed = this.sizeRatio * baseSpeed
  rotSpeed = this.sizeRatio * baseRotation

  constructor(element: HTMLElement) {
    this.element = element

    this.point = new paper.Point({
      x: random(0, this.element.offsetWidth),
      y: random(0, this.element.offsetHeight / 2)
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

    if (this.path.position.y < this.element.offsetHeight + this.radius2) {
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
      starArr.push(new Star(this.element))

    this.done = true
  }

}

const appDiv = document.getElementById("app")
const canvas = document.createElement("canvas") as HTMLCanvasElement
appDiv?.appendChild(canvas)

canvas.width = window.innerWidth
canvas.height = window.innerHeight

paper.setup(canvas)

const numWanted = 75

for (let i = 0; i < numWanted; i++) {
  const star = new Star(canvas)
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
canvas[onresize] {
  margin: 0px;
  padding: 0px;
  display: block;
  position: absolute;
  width: 100%;
  height: 100%;
  z-index: -2;
}
</style>

<template>
</template>