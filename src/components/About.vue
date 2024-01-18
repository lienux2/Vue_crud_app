<script setup lang="ts"></script>

<template>
  <div>
    <div class="title">
      <h1 class="main-title">About</h1>
    </div>
  </div>
  <div>
    <div class="text">
      <p class="main-text">
        This project is simple CRUD app using Vue.js. You can add post, delete
        post, edit post. You can also see all posts on one page and each has
        single page view. Json-server is used for data storage, and axios
        methods to get those data. Also - added iconify to use some icons which
        can be seen in single post view.
      </p>
    </div>
  </div>
</template>

<style scoped>
.title {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 50px;
}

.main-title {
  font-size: 80px;
  color: bisque;
}

.text {
  display: flex;
  justify-content: center;
  padding: 0 250px;
}

.main-text {
  text-align: center;
  font-size: 40px;
}

@media (max-width: 2000px) {
  .text {
    padding: 0 150px;
  }

  .main-title {
    font-size: 50px;
  }

  .main-text {
    font-size: 30px;
  }
}

@media (max-width: 1200px) {
  .text {
    padding: 0 80px;
  }
}

@media (max-width: 600px) {
  .text {
    padding: 0 30px;
  }
}
</style>
