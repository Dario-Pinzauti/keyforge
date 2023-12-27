<template>
  <div class="h-1/2 w-1/4 bg-slate-500 rounded-xl pr-2">
    <h3 class="text-center">Player1</h3>
    <div class="flex items-center justify-between">
      <img
        :src="keyArray[keyIndex]"
        alt=""
        style="transform: rotate(90deg); height: 175px; padding: 0px; border: 0px"
      />
      <div class="flex gap-1">
        <button class="w-10 h-7 bg-slate-600 rounded-md" @click="decrementKey">-</button>
        <button class="w-10 h-7 bg-slate-600 rounded-md" @click="incrementKey">+</button>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, reactive } from 'vue';

const keyIndex = ref(0);
const keyArray = reactive(['/keyempty.png', '/key1.png', '/key2.png', '/keyfull.png']);

const incrementKey = () => {
  if (keyIndex.value <= 2) {
    keyIndex.value++;
  }
};

const decrementKey = () => {
  if (keyIndex.value > 0) {
    keyIndex.value--;
  }
};
</script>

<style scoped></style>
