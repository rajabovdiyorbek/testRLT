<template>
  <div class="side-component">
    <img src="../assets/img/nicebg.jpg" alt="sidebar img" />
  </div>
</template>

<script setup></script>

<style lang="scss" scoped>
.side-component {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
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
