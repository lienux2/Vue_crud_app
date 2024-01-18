<script setup lang="ts">
import AddPost from "../components/AddPost.vue";
import axios from "axios";
import { useRouter } from "vue-router";

const router = useRouter();

const createPost = async (newPost: string[]) => {
  await axios.post("http://localhost:3000/posts", newPost).then((data) => {
    alert("Post has been created!"); //replace with toastify
    router.push("/");
    return data;
  });
};
</script>

<template>
  <AddPost @create-post="createPost" />
</template>

<style scoped></style>
