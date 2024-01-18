<script setup lang="ts">
import axios from "axios";
import Posts from "../components/Posts.vue";
import { onMounted, ref } from "vue";

let posts = ref([]);

const seeAllPosts = () => {
  axios.get("http://localhost:3000/posts").then(({ data }) => {
    console.log(data);
    posts.value = data;
  });
};

onMounted(async () => {
  seeAllPosts();
});
</script>

<template>
  <Posts :posts="posts" />
</template>
