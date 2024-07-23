<template>
  <div>
    <h3>Список предметов</h3>
    <PostItem v-for="post in posts" :key="post.id" :post="post" />
  </div>
</template>

<script setup>
import PostItem from "./PostItem.vue";

defineProps({
  posts: Array,
  require: true,
});
</script>

<style scoped>
</style>
