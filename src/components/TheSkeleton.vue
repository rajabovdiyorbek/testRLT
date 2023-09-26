<template>
  <div
    class="skeleton"
    :style="{ width: `${width}px`, height: `${height}px` }"
  ></div>
</template>

<script setup>
import { defineProps } from "vue";
defineProps(["width", "height"]);
</script>

<style scoped lang="scss">
.skeleton {
  width: 100%;
  border-radius: 8px;
  margin-top: 16px !important;
  margin: auto;
  background: linear-gradient(90deg, #3c3c3c 0%, #444 51.04%, #333 100%);
  background-size: 200% 100%;
  animation: loading 1.5s infinite;

  @keyframes loading {
    0% {
      background-position: 200% 0;
    }
    100% {
      background-position: -200% 0;
    }
  }

  &.custom-styles {
    // Дополнительные пользовательские стили могут быть добавлены здесь
  }
}
</style>
