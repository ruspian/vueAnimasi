<script setup>
import { ref } from 'vue';
import gsap from 'gsap';

const tasks = ref(['Belajar HTML', 'Belajar JavaScript', 'Belajar Vue']);
const taskBaru = ref('');

function tambahTask() {
    if(taskBaru.value) {
        tasks.value.unshift(taskBaru.value);
        taskBaru.value = '';
    }
}

function hapusTask(index) {
    tasks.value.splice(index, 1);
}

function beforeEnter(el) {
    el.style.opacity = 0;
    el.style.transform = 'translateX(-30px)';
}

function enter(el) {
    gsap.to(el, {
        duration: 0.5,
        x: 0,
        opacity: 1,
        delay: el.dataset.index * 0.1
    })
}


function afterEnter(el) {
    gsap.to(el, {
        duration: 0.5,
        x: 0,
        opacity: 1
    })
}

function beforeLeave(el) {
    el.style.opacity = 1;
    el.style.transform = 'translateX(0)';
}

function afterLeave(el) {
    el.style.opacity = 0;
    el.style.transform = 'translateX(30px)';
}
</script>

<template>
  <main>
    <div class="container">
      <input
        type="text"
        autofocus
        v-model="taskBaru"
        @keyup.enter="tambahTask()"
      />
      <!-- membuat animasi masuk dan keluar menggunakan transitionGroup -->
      <TransitionGroup
        name="fade"
        appear
        @before-enter="beforeEnter"
        @enter="enter"
        @after-enter="afterEnter"
        @before-leave="beforeLeave"
        @after-leave="afterLeave"
      >
        <div
          class="card-list"
          v-for="(task, index) in tasks"
          :key="task"
          :data-index="index"
          @click="hapusTask(tasks.indexOf(task))"
        >
          {{ task }}
        </div>
      </TransitionGroup>
    </div>
  </main>
</template>

<style scoped>
.container {
  margin: 0 auto;
}

.container input {
  width: 100%;
  padding: 10px;
  border-radius: 5px;
  border: 1px solid #ccc;
  margin-bottom: 10px;
  box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.1);
}

.card-list {
  width: 100%;
  padding: 5px 10px;
  margin-top: 10px;
  border-radius: 5px;
  border: 1px solid #ccc;
  text-align: center;
  box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.1);
  cursor: pointer;
}

/* animasi masuk
.fade-enter-from {
  opacity: 0;
  transform: scale(0.6);
}

.fade-enter-to {
  opacity: 1;
  transform: scale(1);
}

.fade-enter-active {
  transition: all 0.5s ease;
} */

/* animasi keluar */
/* .fade-move {
  transition: all 0.5s ease;
} */
</style>
