<script setup lang="ts">
import EditIcon from "../components/icons/IconEdit.vue";
import SaveIcon from "../components/icons/IconSave.vue";
import DeleteIcon from "../components/icons/IconDelete.vue";
import { ref } from "vue";

defineProps({
  post: {
    type: Object,
    required: true,
  },
});

defineEmits(["delete-post", "edited-post", "toggle-edit"]);

const isEditing = ref(false);
</script>

<template>
  <div class="container">
    <div class="card">
      <div class="card-info">
        <label v-if="isEditing" for="image">Image URL</label>
        <input v-if="isEditing" type="text" id="image" v-model="post.image" />
        <img class="image" v-else :src="post.image" alt="" />
        <label for="destination" v-if="isEditing">Destination</label>
        <input
          v-if="isEditing"
          type="text"
          v-model="post.destination"
          id="destination"
        />
        <h1 v-else>{{ post.destination }}</h1>
      </div>
      <div class="card-info">
        <label for="city" v-if="isEditing">City</label>
        <input
          id="city"
          v-if="isEditing"
          type="text"
          v-model="post.city"
          @input="$emit('edited-post', post.city)"
        />
        <label for="country" v-if="isEditing">Country</label>
        <input
          id="country"
          v-if="isEditing"
          type="text"
          v-model="post.country"
          @input="$emit('edited-post', post.country)"
        />
        <p v-else>Located in {{ post.city }}, {{ post.country }}</p>
        <label for="description" v-if="isEditing">Description</label>
        <textarea
          v-if="isEditing"
          type="text"
          v-model="post.description"
          @input="$emit('edited-post', post.description)"
          id="description"
          cols="60"
          rows="5"
        ></textarea>
        <p v-else class="description">
          {{ post.description }}
        </p>
        <label for="rating" v-if="isEditing">Rating</label>
        <input
          id="rating"
          v-if="isEditing"
          type="text"
          v-model="post.rating"
          @input="$emit('edited-post', post.rating)"
        />
        <p v-else>Rating: {{ post.rating }}</p>
      </div>
    </div>
    <div class="card-options">
      <EditIcon v-if="!isEditing" @click="isEditing = !isEditing" />
      <SaveIcon
        v-else
        @click="$emit('edited-post', post.id, post), (isEditing = !isEditing)"
      />
      <DeleteIcon @click="$emit('delete-post', post.id)" />
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin: 50px 0;
}

.image {
  margin: 0 auto;
}

.card {
  display: flex;
  flex-direction: column;
  text-align: center;
  gap: 20px;
  padding: 20px;
}

.card-info {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.card-options {
  display: flex;
  gap: 50px;
}

.description {
  max-width: 1000px;
}

@media (max-width: 850px) {
  img {
    width: 500px;
  }
}

@media (max-width: 600px) {
  img {
    width: 300px;
  }
}
</style>
