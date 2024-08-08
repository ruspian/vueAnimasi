<script setup>
import { RouterLink } from "vue-router";
</script>

<template>
  <header class="container">
    <RouterLink :active-class="'active'" to="/">Home</RouterLink>
    <RouterLink :active-class="'active'" to="/about">About</RouterLink>
  </header>
</template>

<style scoped>
header {
  padding: 20px;
  display: flex;
  gap: 20px;
}

.active {
  font-weight: bold;
  color: white;
  background-color: green;
  padding: 5px 10px;
  border-radius: 5px;
  text-decoration: none;
}
</style>
