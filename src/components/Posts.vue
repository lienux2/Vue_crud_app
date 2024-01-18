<script setup lang="ts">
import Button from "../components/Button.vue";

const props = defineProps({
  posts: {
    type: Object,
    required: true,
  },
});
</script>

<template>
  <div class="container" v-if="posts">
    <div class="card" v-for="post of posts">
      <div>
        <img class="image" :src="post.image" alt="" />
      </div>
      <div class="card-info">
        <h1>{{ post.destination }}</h1>
        <RouterLink :to="`/post/${post.id}`">
          <Button @click="$emit('get-id', `{{ post.id }}`)">See post</Button>
        </RouterLink>
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  justify-content: center;
  row-gap: 100px;
  column-gap: 100px;
  margin: 20px;
}

.card {
  display: flex;
  flex-direction: column;
}
.card-info {
  display: flex;
  justify-content: space-evenly;
  padding: 20px 20px;
}

.image {
  width: 300px;
  aspect-ratio: 1 / 1;
}

@media (max-width: 800px) {
  .container {
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    margin: 0 120px 0 150px;
  }
}

@media (max-width: 400px) {
  .container {
    display: grid;
    justify-content: right;
    row-gap: 100px;
    column-gap: 100px;
    margin: 5px;
  }

  .image {
    width: 250px;
    aspect-ratio: 1 / 1;
  }
}

@media (max-width: 375px) {
  .container {
    display: grid;
    justify-content: right;
    row-gap: 100px;
    column-gap: 100px;
    margin: 5px;
  }
}
</style>
