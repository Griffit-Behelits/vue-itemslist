<template>
  <form class="form" @submit.prevent="">
    <h2>Создание поста предмета</h2>
    <input
      class="input"
      v-model.trim="post.title"
      type="text"
      placeholder="Название предмета"
    />
    <input
      class="input"
      v-model.trim="post.description"
      type="text"
      placeholder="Описание предмета"
    />
    <MyButton @click="createPost">Создать</MyButton>
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
.input {
  width: 100%;
  border: 2px solid #5e330e;
  padding: 10px;
  margin-top: 10px;
}
</style>
