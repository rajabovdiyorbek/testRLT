<template>
  <div class="modal-wrapper">
    <div class="close-button" @click="close">
      <img src="../assets/icons/close-icon.svg" />
    </div>
    <div class="modal-content">
      <img
        :src="require(`../assets/img/item-${props.selectedItem.content}.svg`)"
        alt=""
      />
      <div class="modal-content__sceleton">
        <TheSkeleton :width="200" :height="30" />
        <TheSkeleton :width="200" :height="10" />
        <TheSkeleton :width="200" :height="10" />
        <TheSkeleton :width="200" :height="10" />
        <TheSkeleton :width="180" :height="10" />
        <TheSkeleton :width="80" :height="10" />
      </div>

      <div v-if="props.slug" class="count">
        <input
          type="text"
          v-model="updatedCount"
          placeholder="Введите количество"
        />
        <div class="count-btns">
          <button class="light-btn" @click="close">Отмена</button>
          <button class="red-btn" @click="update(props.selectedItem.id)">
            Подтвердить
          </button>
        </div>
      </div>
      <button
        class="delete-btn"
        v-else
        @click="deleteItem(props.selectedItem.id)"
      >
        Удалить предмет
      </button>
    </div>
  </div>
</template>

<script setup>
import { ref, defineEmits, defineProps } from "vue";
import TheSkeleton from "./TheSkeleton.vue";
const props = defineProps(["selectedItem", "slug"]);
const emit = defineEmits(["close", "delete"]);
const updatedCount = ref("");
const count = ref(props.selectedItem.count);

const deleteItem = (itemId) => {
  const newCount = count.value - 1;
  emit("delete", { itemId, newCount });
  emit("close", false);
};
const update = (itemId) => {
  emit("update", { itemId, updatedCount });
  emit("close", false);
};
const close = () => {
  emit("close", false);
};
</script>

<style lang="scss" scoped>
.modal {
  &-wrapper {
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
    overflow: hidden;
  }
  &-content {
    img {
      width: 130px;
      height: 130px;
      margin: 55px 60px 30px 60px;
    }
    .delete-btn {
      width: 220px;
      color: white;
      background: #fa7272;
      padding: 11px 55px;
      font-style: 14px;
      border: none;
      border-radius: 8px;
      margin: 18px 15px;
      cursor: pointer;
    }
    .delete-btn:hover {
      background: #f88;
    }
    &__sceleton {
      margin: auto;
      width: 210px;
      height: 208px;
      border-top: 1px solid #4d4d4d;
      border-bottom: 1px solid #4d4d4d;
      color: white;
    }
  }
}
.count {
  position: relative;
  bottom: 60px;
  padding: 20px;
  width: 252px;
  height: 133px;
  z-index: 10;
  border-top: 1px solid #4d4d4d;
  background: rgba(38, 38, 38, 0.6);
  input {
    width: 220px;
    height: 40px;
    border-radius: 4px;
    padding: 11px;
    margin-bottom: 20px;
    border: 1px solid #4d4d4d;
    outline: none;
    background: #262626;
    color: white;
  }
  .count-btns {
    display: flex;
    gap: 5px;
    .light-btn {
      padding: 8px 28px;
      background: #fff;
      color: #2d2d2d;
      border-radius: 12px;
      border: none;
      cursor: pointer;
    }
    .red-btn {
      padding: 8px 15px;
      color: white;
      background: #fa7272;
      border: none;
      border-radius: 12px;
      cursor: pointer;
    }
  }
}
</style>
