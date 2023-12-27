<script setup>
import { reactive, ref } from 'vue';
import PlayerCard from './components/PlayerCard.vue';

const emberNumber = ref(0);
const keyNumber = ref(0);
const key = reactive(['/keyempty.png', '/key1.png', '/key2.png', '/keyfull.png']);

const increment = () => {
  emberNumber.value++;
};

const decrement = () => {
  emberNumber.value--;
};

const keyIncrement = () => {
  if (keyNumber.value == 3) {
    keyNumber.value = 0;
    return;
  }
  keyNumber.value++;
};
const keyDecrement = () => {
  if (keyNumber.value == 0) {
    keyNumber.value = 3;
    return;
  }
  keyNumber.value--;
};

const forge = () => {
  if (emberNumber.value < 6) {
    return;
  }
  emberNumber.value = emberNumber.value - 6;
  keyNumber.value++;
};
</script>

<template>
  <div class="h-screen w-screen box-content m-0 p-4 flex gap-2">
    <!-- <div>
      <img :src="key[keyNumber]" class="logo" alt="Vite logo" />
      <div style="text-align: center">
        <button @click="keyIncrement">+</button>
        <button @click="keyDecrement">-</button>
      </div>
    </div>
    <div class="ember">
      <img src="/ember.png" class="emberImage" />
      <div style="text-align: center">
        <p>{{ emberNumber }}</p>
        <button @click="increment">+</button>
        <button @click="decrement">-</button>
        <button @click="forge">forgia</button>
      </div>
    </div> -->
    <PlayerCard></PlayerCard>
    <PlayerCard></PlayerCard>
  </div>
</template>

<style scoped></style>
