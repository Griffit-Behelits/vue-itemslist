<template>
  <div class="app">
    <h2>Страница с постами</h2>
    <PostForm @create="createPost" />
    <MySelect v-model="selectedSort" :options="sortOptions" />
    <PostList v-if="loadPosts" :posts="posts" @remove="removePost" />
    <div v-else>Идет загрузка постов...</div>
  </div>
</template>

<script setup>
import PostList from "./components/PostList.vue";
import PostForm from "./components/PostForm.vue";
import MySelect from "./components/UI/MySelect.vue";
import axios from "axios";
import { onMounted, ref } from "vue";
import { watch } from "vue";

const posts = ref([]);
const loadPosts = ref(false);

const createPost = (post) => {
  posts.value.push(post);
  console.log(posts);
};

const removePost = (post) => {
  posts.value = posts.value.filter((p) => p.id !== post.id);
};

const fetchPost = async () => {
  try {
    setTimeout(async () => {
      const res = await axios.get("https://a1c7306a4c03515b.mokky.dev/posts");
      posts.value = res.data;
      loadPosts.value = true;
    }, 1000);
  } catch (error) {
    console.log(error, error.message);
  } finally {
    loadPosts.value = false;
  }
};
const selectedSort = ref("");
const sortOptions = ref([
  { value: "title", name: "По названию" },
  { value: "description", name: "По описанию" },
]);

onMounted(fetchPost);
watch(selectedSort, (newValue) => {
  console.log(newValue)
  // posts.value.sort((post1, post2) => {
  //   return post1[newValue]?.localeCompare(post2[newValue]);
  // });
});
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
