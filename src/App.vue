<script setup>
import { RouterView } from 'vue-router'
import Header from './components/Header.vue';
</script>

<template>
  <main>
    <Header />
    <div>
      <Transition name="route">
        <RouterView />
      </Transition>
    </div>
  </main>
</template>

<style scoped>
main {
  width: 90vw;
  height: 90vh;
  padding: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

div {
  margin-top: 20px;
}

.route-enter-from {
  opacity: 0;
  transform: translateX(-30px);
}

.route-enter-to {
  opacity: 1;
  transform: translateX(0);
}

.route-enter-active {
  transition: all 0.3s ease;
}


</style>
