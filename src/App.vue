<script setup lang="ts">
import StarFall from "./components/starFall.vue";
import Image from "./components/Image.vue";

onclick = (event) => {
  console.log(`${event.clientX}, ${event.clientY}`)
};

const julianSrc = './src/assets/julian-stuff/'
const assets = './src/assets/'

</script>

<template>
  <StarFall class="overlay" background-color="#1a1a1a">

    <div id="imageColumnLeft">
      <Image :dir=assets filename="butterflies.gif"></Image>
      <Image :dir=assets filename="gnome-toilet.gif"></Image>
      <Image :dir=assets filename="apple.gif"></Image>
      <Image :dir=assets filename="sharkie.gif"></Image>
    </div>

    <div id="centerContent">
      <img src="./assets/julian-stuff/julianlogo.gif" class="logo" alt="julian awesome website logo"/>
      <h2>omg hello welcome to julian awesome epic website!!!!</h2>

      <p>hello dear visitor! this is an early version of my website!
        I plan on adding a lot more so you can fully immerse yourself in the julian experience!</p>


      <!--      <ImageGrid dir="./src/assets/julian-stuff/" :images=imageGridArr>-->
      <!--        -->

      <!--      </ImageGrid>-->

      <div id="julianPics">
        <Image id="matrix" :dir=julianSrc filename="julianmatrix.png"></Image>
        <Image id="pants" :dir=julianSrc filename="julianpants.png"></Image>
        <Image id="fairy" :dir=julianSrc filename="julianfairy.png"></Image>
        <Image id="epic" :dir=julianSrc filename="le epic face.png"></Image>
        <Image id="camera" :dir=julianSrc filename="juliancamera.png"></Image>
        <!--        <Image id="face" :dir=julianSrc filename="julianface.png"></Image>-->
      </div>

      <div id="introText">
        <h2 style="display: inline-block">hello i am

          <Image :dir=julianSrc filename="julian shuster.gif" width="25%"></Image>
        </h2>

      </div>
    </div>
    <div id="imageColumnRight">
      <Image :dir=assets filename="flying-saucer.gif"></Image>
      <Image :dir=assets filename="fish-graphic.gif"></Image>
      <Image :dir=assets filename="lightbulb.gif"></Image>
      <Image :dir=assets filename="cactus.gif"></Image>
    </div>

  </StarFall>
</template>

<style scoped>
.logo {
  padding-top: 40px;
  padding-bottom: 20px;
  will-change: filter;
  transition: filter 300ms;
  width: fit-content;
  align-self: center;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #89DD36);
}

.overlay {
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  display: grid;
  grid-template-columns: auto 1fr auto;
  grid-gap: 10px;
  background: rgba(0, 0, 0, .75);
  width: 100vw;
  height: 100%;
}

#julianPics {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(3, 0.5fr);
  grid-auto-flow: row dense;
  height: fit-content;
  max-width: 1200px;
  justify-items: center;
  padding: 20px;
}

#julianPics img {
  max-width: 75%; /* Ensures images fill their containers */
  height: auto;
}

#fairy {
  grid-area: 1 / 1 / 2 / 2;
}

#epic {
  grid-area: 1 / 2 / 2 / 3;
}

#face {
  grid-area: 2 / 1 / 3 / 2;
}

#camera {
  grid-area: 2 / 2 / 4 / 3;
}

#matrix {
  grid-area: 1 / 3 / 4 / span 5;
}

#pants {
  grid-area: 2 / 1 / 4 / 2;
}

#centerContent {
  display: flex;
  margin: 0 auto;
  flex-direction: column;
  max-width: fit-content;
  height: fit-content;
  justify-content: center;
}

#imageColumnLeft, #imageColumnRight {
  top: 0;
  bottom: 0;
  display: flex;
  flex: 50%;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
  width: fit-content;
  min-width: 300px;
  height: 100%;
}

#imageColumnLeft {
  left: 0;
}

#imageColumnRight {
  right: 0;
}

p {
  color: white;
  max-width: 1280px;
  margin: 0 auto;
  padding: 10px;
}

h1, h2 {
  color: white;
  margin: 0 auto;
  text-align: center;
  padding: 10px;
}
</style>
