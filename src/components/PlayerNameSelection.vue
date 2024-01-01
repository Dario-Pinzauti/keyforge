<template>
  <div
    class="w-screen h-screen absolute bg-slate-600/95 flex justify-center items-center"
    @keyup.enter="createPlayer"
    @keyup.esc="exit"
  >
    <div class="w-1/2 h-14 flex gap-2">
      <div class="rounded-xl bg-slate-800 grow py-2 px-4">
        <input
          type="text"
          name=""
          id=""
          class="grow h-full w-full bg-transparent outline-none text-white text-4xl"
          v-model="playerName"
          autofocus
        />
      </div>
      <button
        class="grow-0 h-full bg-slate-800 hover:bg-slate-700 rounded-xl w-44 text-3xl text-white tracking-wider"
        @click="createPlayer"
      >
        CREA
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const emits = defineEmits(['create', 'exit']);

const playerName = ref('');

const createPlayer = () => {
  emits('create', playerName.value);
};

const exit = () => {
  emits('exit');
};
</script>

<style scoped></style>
