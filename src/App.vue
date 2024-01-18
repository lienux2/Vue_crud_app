<script setup lang="ts">
import Navbar from "./components/Navbar.vue";
import { RouterView } from "vue-router";
</script>

<template>
  <section>
    <Navbar />
  </section>

  <section>
    <RouterView />
  </section>
</template>

<style scoped></style>
