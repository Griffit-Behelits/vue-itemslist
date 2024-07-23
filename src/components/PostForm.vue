<template>
  <form class="form" @submit.prevent="">
    <h2>Создание поста предмета</h2>
    <input
      v-model="post.title"
      class="input"
      type="text"
      placeholder="Название предмета"
    />
    <input
      v-model="post.description"
      class="input"
      type="text"
      placeholder="Описание предмета"
    />
    <button class="btn" @click="createPost">Создать</button>
  </form>
</template>

<script setup>
import { ref } from "vue";

const emit = defineEmits({
  create: null,
});

const id = ref(0);
const post = ref({
  title: "",
  description: "",
});
const clearInputs = () => {
  post.value.title = "";
  post.value.description = "";
};
const createPost = () => {
  post.value.id = id.value++;
  emit("create", { ...post.value });
  clearInputs();
};
</script>

<style scoped>
.form {
  display: flex;
  flex-direction: column;
}
.btn {
  align-self: flex-end;
  margin-top: 5px;
  padding: 10px 10px;
  background: #5e330e;
  border: 1px solid #0d0d0d;
  cursor: pointer;
  transition: 0.3s ease;
}
.btn:hover {
  background: #0d0d0d;
  border: 1px solid #5e330e;
  color: #fff;
}
.input {
  width: 100%;
  border: 2px solid #5e330e;
  padding: 10px;
  margin-top: 10px;
}
</style>
