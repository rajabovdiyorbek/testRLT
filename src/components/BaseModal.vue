<template>
  <div class="modal-wrapper">
    <div class="close-button" @click="close">
      <img src="../assets/icons/close-icon.svg" />
    </div>
  </div>
</template>

<script setup>
import { defineEmits } from "vue";
const emit = defineEmits(["close"]);

const close = () => {
  emit("close", false);
};
</script>

<style lang="scss" scoped>
.modal-wrapper {
  position: absolute;
  right: 0;
  top: 0;
  width: 250px;
  height: 500px;
  border: 1px solid var(--Primary-Border, #4d4d4d);
  border-top-right-radius: 12px;
  border-bottom-right-radius: 12px;
  background: rgba(38, 38, 38, 0.5);
  backdrop-filter: blur(8px);
}
</style>
