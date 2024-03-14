<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
import Image from "./components/Image.vue";
</script>

<template>
  <main>
    <img src="./assets/julianlogo.gif" class="logo" alt="julian awesome website logo"/>

    <h1>omg hello welcome to julian awesome epic website!!!!</h1>
    <!--  <HelloWorld msg="Vite + Vue" />-->
    <!--  <Image filename="space.gif"/>-->
  </main>

</template>

<style scoped>
.logo {
  border-radius: 40px;
  padding: 20px;
  will-change: filter;
  transition: filter 300ms;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #89DD36);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}

h1 {
  color: white;
  max-width: 1280px;
  margin: 0 auto;
  text-align: center;
}

main {
  padding: 2rem;
  align-self: auto;
  text-align: center;

  width: 100vw;
  height: 100vh;
  background-repeat: no-repeat;
  background-image: url("./assets/greenstar.gif");
  background-size: cover
}
</style>
