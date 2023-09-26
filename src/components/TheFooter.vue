<template>
  <div class="footer">
    <div class="footer-content">
      <TheSkeleton :width="699" :height="36" />
    </div>
    <div class="close-button">
      <img src="../assets/icons/close-icon.svg" />
    </div>
  </div>
</template>

<script setup>
import TheSkeleton from "./TheSkeleton.vue";
</script>

<style lang="scss" scoped>
.footer {
  position: relative;
  min-width: 100%;
  min-height: 72px;
  border-radius: 12px;
  margin-top: 24px;
  border: 1px solid var(--Primary-Border, #4d4d4d);
  background: var(--Secondary-BG, #262626);
  &-content {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
    color: white;
  }
}
</style>
