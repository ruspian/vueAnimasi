<script setup>
import { RouterView } from 'vue-router'
import Header from './components/Header.vue';
</script>

<template>
  <main>
    <Header />
    <div>
      <RouterView />
    </div>
  </main>
</template>

<style scoped>
main {
  padding: 20px;
}

div {
  margin-top: 20px;
}
</style>
