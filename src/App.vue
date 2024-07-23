<template>
  <div class="app">
    <PostForm @create="createPost" />
    <PostList :posts="posts" />
  </div>
</template>

<script setup>
import PostList from "./components/PostList.vue";
import PostForm from "./components/PostForm.vue";
import { ref } from "vue";

const posts = ref([]);

const createPost = (post) => {
  posts.value.push(post);
  console.log(posts);
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.app {
  padding: 20px;
}
</style>
