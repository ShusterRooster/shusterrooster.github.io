<script setup lang="ts">
import StarFall from "./components/starFall.vue";
import Image from "./components/Image.vue";

onclick = (event) => {
  console.log(`${event.clientX}, ${event.clientY}`)
};

</script>

<template>
  <main id="main">
    <star-fall></star-fall>
    <div class="overlay">

      <div id="topText">
        <img src="./assets/julian-stuff/julianlogo.gif" class="logo" alt="julian awesome website logo"/>
        <h2>omg hello welcome to julian awesome epic website!!!!</h2>

        <p>hello dear visitor! this is an early version of my website!
          I plan on adding a lot more so you can fully immerse yourself in the julian experience!</p>

        <div id="imageColumnLeft">
          <Image filename="./src/assets/butterflies.gif"></Image>
          <Image filename="./src/assets/gnome-toilet.gif" top="100px"></Image>
        </div>

        <div id="imageColumnRight">
          <Image filename="./src/assets/flying-saucer.gif"></Image>
          <Image filename="src/assets/fish-graphic.gif" top="280px"></Image>
        </div>

        <div id="julianPics">
          <Image filename="./src/assets/julian-stuff/julianfairy.png" left="10px" width="10%" position="absolute"></Image>
          <Image filename="./src/assets/julian-stuff/julianpants.png" top="100px" left="275px" width="10%" position="absolute"></Image>
          <Image filename="./src/assets/julian-stuff/le epic face.png" top="100px" right="325px" width="20%" position="absolute"></Image>
          <Image filename="./src/assets/julian-stuff/julianmatrix.png" top="0" right="25px" width="25%" position="absolute"></Image>
          <Image filename="./src/assets/julian-stuff/julianface.png" top="300px" left="25px" width="20%" position="absolute"></Image>
          <Image filename="./src/assets/julian-stuff/juliancamera.png" top="325px" left="400px" width="15%" position="absolute"></Image>
        </div>

      </div>

      <div id="introText">
        <h2 style="display: inline-block">hello i am

          <Image filename="./src/assets/julian-stuff/julian shuster.gif" width="25%"></Image>
        </h2>

      </div>

    </div>

  </main>

</template>

<style scoped>
.logo {
  padding-top: 40px;
  padding-bottom: 20px;
  will-change: filter;
  transition: filter 300ms;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #89DD36);
}


.overlay {
  position: absolute;
  background: rgba(0,0,0,.75);
  width: 100vw;
  height: 100vh;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}


#topText, #introText {
  position: relative;
  display: block;
  width: fit-content;
  height: fit-content;
  margin: auto;
}

#julianPics {
  position: absolute;
  display: block;
  padding: 20px;
  margin: auto;
  height: 700px;
  overflow: hidden;
  width: 100%;
}

#imageColumnLeft {
  position: relative;
  width: fit-content;
  float: left;
  left: -50%;
}

#imageColumnRight {
  position: relative;
  width: fit-content;
  float: right;
  left: 50%;
}

#introText {
  position: relative;
}

p {
  color: white;
  max-width: 1280px;
  margin: 0 auto;
  padding: 10px;
}

h1, h2 {
  color: white;
  max-width: 1280px;
  margin: 0 auto;
  text-align: center;
  padding: 10px;
}

main {
  align-self: auto;
  text-align: center;
  width: 100%;
  height: 100%;
}
</style>
