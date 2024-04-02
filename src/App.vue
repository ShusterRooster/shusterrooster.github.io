<script setup lang="ts">
import StarFall from "./components/starFall.vue";
import Image from "./components/Image.vue";
import ImageGrid from "./components/ImageGrid.vue";

onclick = (event) => {
  console.log(`${event.clientX}, ${event.clientY}`)
};

const imageGridArr = ['juliancamera.png', 'julianfairy.png', 'julianpants.png',
  'le epic face.png', 'julianmatrix.png', 'julianface.png']

</script>

<template>
  <div class="overlay">

    <div id="imageColumnLeft">
      <Image filename="./src/assets/butterflies.gif"></Image>
      <Image filename="./src/assets/gnome-toilet.gif"></Image>
    </div>

    <div id="centerContent">
      <img src="./assets/julian-stuff/julianlogo.gif" class="logo" alt="julian awesome website logo"/>
      <h2>omg hello welcome to julian awesome epic website!!!!</h2>

      <p>hello dear visitor! this is an early version of my website!
        I plan on adding a lot more so you can fully immerse yourself in the julian experience!</p>


      <ImageGrid dir="./src/assets/julian-stuff/" :images=imageGridArr>
        <!--        <Image filename="./src/assets/julian-stuff/juliancamera.png" width="15%"></Image>-->
        <!--        <Image filename="./src/assets/julian-stuff/julianfairy.png" width="10%"></Image>-->
        <!--        <Image filename="./src/assets/julian-stuff/julianpants.png" width="10%"></Image>-->
        <!--        <Image filename="./src/assets/julian-stuff/le epic face.png" width="20%"></Image>-->
        <!--        <Image filename="./src/assets/julian-stuff/julianmatrix.png" width="25%"></Image>-->
        <!--        <Image filename="./src/assets/julian-stuff/julianface.png" width="20%"></Image>-->

      </ImageGrid>

      <!--      <div id="introText">-->
      <!--        <h2 style="display: inline-block">hello i am-->

      <!--          <Image filename="./src/assets/julian-stuff/julian shuster.gif" width="25%"></Image>-->
      <!--        </h2>-->

      <!--      </div>-->



      <!--    <star-fall></star-fall>-->

    </div>
    <div id="imageColumnRight">
      <Image filename="./src/assets/flying-saucer.gif"></Image>
      <Image filename="src/assets/fish-graphic.gif"></Image>
    </div>
  </div>

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
  flex: 0 0 auto;
  display: grid;
  grid-template-columns: auto 1fr auto;
  grid-gap: 10px;
  margin: 0;
  background: rgba(0, 0, 0, .75);
  width: 100vw;
  height: 100%;
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
