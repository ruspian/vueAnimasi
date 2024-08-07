<script setup>
import { RouterLink, RouterView } from "vue-router";
</script>

<template>
  <div>
    <RouterLink :active-class="'active'" to="/">Home</RouterLink>
    <RouterLink :active-class="'active'" to="/about">About</RouterLink>
  </div>
</template>

<style scoped>
div {
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
