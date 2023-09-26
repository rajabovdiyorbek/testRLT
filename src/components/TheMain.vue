<template>
  <div class="main-wrapper">
    <draggable class="main" :list="items" item-key="item" @change="updateItems">
      <div v-for="item in items" :key="item">
        <template
          class="main-item"
          @click="item.count > 0 ? selectItem(item) : (isModal = false)"
        >
          <img
            v-if="item.content"
            :src="require(`../assets/img/item-${item.content}.svg`)"
            alt=""
          />
          <div
            v-if="item.count >= 0"
            class="main-item__count"
            @click.stop="selectItem(item, true)"
          >
            {{ item.count }}
          </div>
        </template>
      </div>
    </draggable>
    <transition-group name="modal"
      ><BaseModal
        v-if="isModal"
        @close="onClose"
        @delete="onDelete"
        @update="onUpdate"
        :selectedItem="selectedItem"
        :slug="slug"
    /></transition-group>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
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
    id: 4,
  },
  {
    id: 5,
  },
  {
    id: 6,
  },
  {
    id: 7,
  },
  {
    id: 8,
  },
  {
    id: 9,
  },
  {
    id: 10,
  },
  {
    id: 11,
  },
  {
    id: 12,
  },
  {
    id: 13,
  },
  {
    id: 14,
  },
  {
    id: 15,
  },
  {
    id: 16,
  },
  {
    id: 17,
  },
  {
    id: 18,
  },
  {
    id: 19,
  },
  {
    id: 20,
  },
  {
    id: 21,
  },
  {
    id: 22,
  },
  {
    id: 23,
  },
  {
    id: 24,
  },
  {
    id: 25,
  },
]);

const saveItemsToLocalStorage = () => {
  localStorage.setItem("items", JSON.stringify(items.value));
};

const loadItemsFromLocalStorage = () => {
  const savedItems = localStorage.getItem("items");
  if (savedItems) {
    items.value = JSON.parse(savedItems);
  }
};

onMounted(() => {
  loadItemsFromLocalStorage();
});

const onClose = (value) => {
  value ? (isModal.value = value) : (isModal.value = !isModal.value);
};
let selectedItem = ref(null);
let slug = ref(false);

const selectItem = (item, count) => {
  if (item.content) {
    selectedItem.value = item;
    count ? (slug.value = count) : (slug.value = false);
    isModal.value = true;
  } else {
    isModal.value = false;
  }
};

const onDelete = ({ itemId, newCount }) => {
  const itemToUpdate = items.value.find((item) => item.id === itemId);
  if (itemToUpdate) {
    itemToUpdate.count = newCount;
    saveItemsToLocalStorage();
  }
};

const onUpdate = ({ itemId, updatedCount }) => {
  const itemToUpdate = items.value.find((item) => item.id === itemId);
  if (itemToUpdate) {
    itemToUpdate.count = updatedCount;
    saveItemsToLocalStorage();
  }
};

const updateItems = () => {
  saveItemsToLocalStorage();
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
    overflow: hidden;
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
  &-item:hover {
    background: #2f2f2f;
  }
}
.modal-enter-active,
.modal-leave-active {
  transition: all 0.5s ease;
}
.modal-enter-from,
.modal-leave-to {
  opacity: 0;
  transform: translateX(100%);
}
</style>
