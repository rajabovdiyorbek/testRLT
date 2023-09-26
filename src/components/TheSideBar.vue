<template>
  <div class="side-component">
    <img src="../assets/img/nicebg.jpg" alt="sidebar img" />
    <TheSkeleton :width="200" :height="30" />
    <TheSkeleton :width="200" :height="10" />
    <TheSkeleton :width="200" :height="10" />
    <TheSkeleton :width="200" :height="10" />
    <TheSkeleton :width="180" :height="10" />
    <TheSkeleton :width="80" :height="10" />
  </div>
</template>

<script setup>
import TheSkeleton from "./TheSkeleton.vue";
</script>

<style lang="scss" scoped>
.side-component {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 236px;
  height: 500px;
  padding: 18px 14px 24px 14px;
  border-radius: 12px;
  border: 1px solid #4d4d4d;
  color: white;
  background: var(--Secondary-BG, #262626);
  img {
    border-radius: 12px;
    filter: blur(5px);
  }
}
</style>
