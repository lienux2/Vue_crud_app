<script setup lang="ts">
import axios from "axios";
import Post from "../components/Post.vue";
import { onMounted, ref } from "vue";
import { useRoute, useRouter } from "vue-router";

const router = useRouter();
let post = ref([]);
const route = useRoute();
const { id } = route.params;

const seeOnePost = (id: string) => {
  axios.get(`http://localhost:3000/posts/${id}`).then(({ data }) => {
    post.value = data;
    console.log(post.value);
  });
};

const editOnePost = (id: string, post: string[]) => {
  axios.put(`http://localhost:3000/posts/${id}`, post).then(({ data }) => {
    alert("Post has been edited!");
  });
};

const deleteOnePost = (id: string) => {
  axios.delete(`http://localhost:3000/posts/${id}`).then(({ data }) => {
    alert("Post has been deleted!");
    router.push("/");
    post.value = data;
  });
};

onMounted(() => {
  return seeOnePost(id as string);
});
</script>

<template>
  <Post
    :post="post"
    :id="id"
    @delete-post="deleteOnePost"
    @edited-post="editOnePost"
  />
</template>
