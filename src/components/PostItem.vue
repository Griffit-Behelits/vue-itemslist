<template>
  <div class="post">
    <div>
      <div>Название: {{ post.title }}</div>
      <div>Описание: {{ post.description }}</div>
    </div>
    <div class="post-btn">
      <MyButton @click="$emit('remove', post)">Удалить</MyButton>
    </div>
  </div>
</template>

<script setup>
defineProps({
  post: Object,
  require: true,
});
</script>

<style scoped>
.post {
  border: 2px solid #5e330e;
  padding: 10px 15px;
  border-radius: 5px;
  background: #0d0d0d;
  color: aliceblue;
  margin-top: 10px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>
