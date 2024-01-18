<template>
  <button>
    <slot> </slot>
  </button>
</template>

<script setup lang="ts"></script>

<style scoped>
button {
  padding: 5px;
  border: transparent;
  border-radius: 12px;
  width: 100px;
  font-weight: bold;
  transition: all 0.5s;
}

button:hover {
  opacity: 0.5;
}
</style>
