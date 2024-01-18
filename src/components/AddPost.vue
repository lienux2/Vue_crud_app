<script setup lang="ts">
import { reactive } from "vue";
import Button from "../components/Button.vue";

let newPost = reactive({
  destination: "",
  country: "",
  city: "",
  image: "",
  description: "",
  rating: "",
});

const emit = defineEmits(["create-post"]);

const createPost = () => {
  emit("create-post", newPost);
};
</script>

<template>
  <div class="form-content">
    <form v-on:submit.prevent="createPost()">
      <h1 class="form-title">Add new travel destination</h1>
      <div class="form-inputs">
        <div class="form-inputs-section">
          <label for="destination">Destination name:</label>
          <input
            type="text"
            id="destination"
            placeholder="Name of destination..."
            v-model="newPost.destination"
          />

          <label for="country">Country:</label>
          <input
            type="text"
            id="country"
            placeholder="Country..."
            v-model="newPost.country"
          />

          <label for="city">City:</label>
          <input
            type="text"
            id="city"
            placeholder="City..."
            v-model="newPost.city"
          />

          <label for="image">Image:</label>
          <input
            type="text"
            id="image"
            placeholder="Image..."
            v-model="newPost.image"
          />
        </div>

        <div class="form-inputs-section">
          <label for="description">Description:</label>
          <textarea
            id="description"
            cols="30"
            rows="7"
            placeholder="Enter description of destination..."
            v-model="newPost.description"
          ></textarea>

          <label for="rating">Rating:</label>
          <input type="number" id="rating" v-model="newPost.rating" />
        </div>
      </div>
      <div class="button-wrapper">
        <Button class="button-add">Create</Button>
      </div>
    </form>
  </div>
</template>

<style scoped>
.form-content {
  display: flex;
  justify-content: center;
}
form {
  text-align: center;
  color: antiquewhite;
  border: 1px solid pink;
  margin: 55px;
  padding: 70px;
  box-shadow: 1px 1px 10px 2px fuchsia;
}

.form-title {
  margin: 20px;
  font-size: 30px;
  color: crimson;
}
.form-inputs {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 70px;
}

.form-inputs-section {
  display: flex;
  flex-direction: column;
  gap: 20px;

  input {
    width: 350px;
  }
}

.button-wrapper {
  margin-top: 50px;
  button {
    background-color: darkgreen;
  }
}

@media (max-width: 1100px) {
  .form-inputs {
    flex-wrap: wrap;
  }

  .form-inputs-section {
    display: flex;
    flex-direction: column;
    gap: 20px;

    input {
      width: 350px;
    }
  }
}

@media (max-width: 700px) {
  .form-inputs {
    flex-wrap: wrap;
  }

  .form-inputs-section {
    gap: 10px;
    input {
      width: 250px;
    }
  }
}

@media (max-width: 600px) {
  .form-inputs {
    flex-wrap: wrap;
  }

  .form-inputs-section {
    gap: 5px;
    input {
      width: 150px;
    }
  }

  textarea {
    width: 150px;
  }
}
</style>
