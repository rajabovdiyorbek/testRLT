<template>
  <div class="wrapper">
    <div class="content">
      <TheSideBar></TheSideBar>
      <TheMain></TheMain>
    </div>
    <TheFooter></TheFooter>
  </div>
</template>

<script setup>
import TheFooter from "./components/TheFooter.vue";
import TheSideBar from "./components/TheSideBar.vue";
import TheMain from "./components/TheMain.vue";
</script>
