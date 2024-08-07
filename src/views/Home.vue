<script setup>
    import { ref } from 'vue';

    const tampilkanTeks = ref(false);
</script>


<template>
    <main>
        <div class="container">
            <Transition name="fade">
                <h1 v-if="tampilkanTeks">Buka Halaman Home</h1>
                <h1 v-else="tampilkanTeks">Tutup Halaman Home</h1>
            </Transition>
            <button @click="tampilkanTeks = !tampilkanTeks" >{{ tampilkanTeks ? 'Tutup' : 'Buka' }}</button>
        </div>
        </main>
</template>


<style scoped>

.container {
    position: relative;
}

h1 {
    position: absolute;
}

.fade-enter-from{
    opacity: 0;
}

.fade-enter-to{
    opacity: 1;
}

.fade-enter-active{
    transition: all 1s ease;
}

.fade-leave-from{
    opacity: 1;
}

.fade-leave-to{
    opacity: 0;
}

.fade-leave-active{
    transition: all 1s ease;
}

button {
    margin-top: 50px;
}
</style>