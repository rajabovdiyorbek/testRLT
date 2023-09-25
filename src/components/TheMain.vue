<template>
  <div class="main-wrapper">
    <draggable class="main" :list="items" item-key="item">
      <div v-for="item in items" :key="item">
        <template
          class="main-item"
          @click="item.content ? onClose() : (isModal = false)"
        >
          <img
            v-if="item.content"
            :src="require(`../assets/img/item-${item.content}.svg`)"
            alt=""
          />
          <div v-if="item.count" class="main-item__count">
            {{ item.count }}
          </div>
        </template>
      </div>
    </draggable>
    <BaseModal v-show="isModal" @close="onClose" />
  </div>
</template>

<script setup>
import { ref } from "vue";
import { VueDraggableNext as draggable } from "vue-draggable-next";
import BaseModal from "./BaseModal.vue";

const isModal = ref(false);
const items = ref([
  {
    id: 1,
    content: "green",
    count: 4,
  },
  {
    id: 2,
    content: "orange",
    count: 5,
  },
  {
    id: 3,
    content: "purple",
    count: 6,
  },
  {
    id: 1,
  },
  {
    id: 2,
  },
  {
    id: 3,
  },
  {
    id: 1,
  },
  {
    id: 2,
  },
  {
    id: 3,
  },
  {
    id: 1,
  },
  {
    id: 2,
  },
  {
    id: 3,
  },
  {
    id: 1,
  },
  {
    id: 2,
  },
  {
    id: 3,
  },
  {
    id: 1,
  },
  {
    id: 2,
  },
  {
    id: 3,
  },
  {
    id: 1,
  },
  {
    id: 2,
  },
  {
    id: 3,
  },
  {
    id: 1,
  },
  {
    id: 2,
  },
  {
    id: 3,
  },
  {
    id: 3,
  },
]);

const onClose = (value) => {
  value ? (isModal.value = value) : (isModal.value = !isModal.value);
};
</script>

<style lang="scss" scoped>
.main {
  background: var(--Secondary-BG, #262626);
  border-radius: 12px;
  border: 1px solid #4d4d4d;
  height: 500px;
  display: grid;
  grid-template-columns: repeat(5, 105px);
  overflow: hidden;
  &-wrapper {
    position: relative;
  }
  &-item {
    position: relative;
    display: flex;
    justify-content: center;
    border: 1px solid #4d4d4d;
    box-sizing: border-box;
    width: 105px;
    height: 100px;
    color: white;
    cursor: pointer;
    img {
      width: 54px;
    }
    &__count {
      position: absolute;
      font-size: 10px;
      bottom: 0;
      right: 0;
      padding: 0px 2px 0px 4px;
      border: 1px solid #4d4d4d;
      border-bottom: none;
      color: #918c8c;
      border-radius: 6px 0px 0px 0px;
    }
  }
}
</style>
