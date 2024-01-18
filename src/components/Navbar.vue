<script setup lang="ts">
import { RouterLink } from "vue-router";
import WorldIcon from "../components/icons/IconWorld.vue";
</script>

<template>
  <header>
    <nav class="navigation">
      <div class="navigation-options">
        <RouterLink to="/"><WorldIcon /></RouterLink>
        <h1>Travel CRUD app</h1>
      </div>
      <div class="navigation-options">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
        <RouterLink to="/add">Create</RouterLink>
      </div>
    </nav>
  </header>
</template>

<style scoped>
header {
  margin: 50px;
}
.logo {
  width: 100px;
}

.navigation {
  display: flex;
  justify-content: space-between;
}

.navigation-options {
  display: flex;
  gap: 30px;
  align-items: center;
  color: #fb2576;
  a {
    text-decoration: none;
    color: inherit;
    font-weight: bolder;
  }
}

@media (max-width: 800px) {
  .navigation {
    justify-content: center;
  }
}

@media (max-width: 600px) {
  .navigation {
    justify-content: center;
    flex-wrap: wrap;
  }

  .logo {
    width: 50px;
  }
}
</style>
