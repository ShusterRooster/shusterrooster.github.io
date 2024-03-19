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
      <div class="text">
        <img src="./assets/julianlogo.gif" class="logo" alt="julian awesome website logo"/>
        <h2>omg hello welcome to julian awesome epic website!!!!</h2>

        <p>hello dear visitor! this is an early version of my website!
          I plan on adding a lot more so you can fully immerse yourself in the julian experience!</p>

      </div>
      <Image filename="butterflies.gif" top="180px" left="180px"></Image>
      <Image filename="flying-saucer.gif" top="170px" left="1270px"></Image>
      <Image filename="gnome-toilet.gif" top="445px" left="100px"></Image>
      <Image filename="fish-graphic.gif" top="380px" left="1310px"></Image>


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

.overlay {
  position: absolute;
  border-radius: 25px;
  background: rgba(0,0,0,.75);;
  width: 100%;
  height: 100%;
  top: 50%;
  left: 50%;
  padding: 20px;
  transform: translate(-50%, -50%);
}

.text {
  left: 300px;
  right: 300px;
  margin-left: 300px;
  margin-right: 300px;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #89DD36);
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
