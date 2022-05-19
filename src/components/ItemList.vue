<script setup>
import { ref } from "vue";

const newItemName = ref("");
const newItemDeadline = ref("");

const items = ref([]);

const addItem = () => {
  items.value.push({
    name: newItemName.value,
    deadline: newItemDeadline.value,
    status: false,
  });
};
</script>

<template>
  <div>
    <div>ItemList</div>
    <h4>みかん</h4>
    <div v-for="item in items" :key="item.name">
      <div
        v-if="item.status == false"
        class="item"
        :class="{ done: item.status == false }"
      >
        <div class="item">
          <div class="name">名前：{{ item.name }}</div>
          <div>{{ item.deadline }}まで</div>
          <a href="#" @click="item.status = true">かんにする</a>
        </div>
      </div>
    </div>
    <div>------------------------------</div>
    <h5>かん</h5>
    <div v-for="item in items" :key="item.name">
      <div v-if="item.status == true">
        <div class="item">
          <div class="name">名前：{{ item.name }}</div>
          <a href="#" @click="item.status = false">みかんにする</a>
        </div>
      </div>
    </div>
    <div>
      <label>
        名前
        <input v-model="newItemName" type="text" />
      </label>
      <label>
        期限
        <input v-model="newItemDeadline" type="time" />
      </label>
      <button @click="addItem">add</button>
    </div>
  </div>
</template>

<style></style>
