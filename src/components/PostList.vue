<template>
  <div v-if="posts.length > 0">
    <h3>Список предметов: {{ posts.length }}</h3>
    <PostItem
      v-for="post in posts"
      :key="post.id"
      :post="post"
      @remove="$emit('remove', post)"
    />
  </div>
  <h2 v-else>Список предметов пуст!</h2>
</template>

<script setup>
import PostItem from "./PostItem.vue";

defineProps({
  posts: Array,
  require: true,
});
</script>

<style scoped></style>
