<template>
  <div class="h-1/2 w-1/3 p-2">
    <div class="flex flex-col w-full h-full bg-slate-500 rounded-xl overflow-hidden justify-start">
      <div class="grow-0 py-3 text-slate-100 text-4xl uppercase tracking-wider">
        <h3 class="text-center" style="font-family: 'Bungee Spice', sans-serif">
          {{ player.name }}
        </h3>
      </div>
      <div class="flex items-center justify-between grow-0 h-1/4 px-3">
        <img :src="keyArray[keyIndex]" class="h-24" />
        <div class="flex gap-1">
          <button
            class="w-16 h-10 bg-slate-600 rounded-md text-2xl flex justify-center items-center"
            @click="decrementKey"
          >
            <icon :icon="mdiMinus" />
          </button>
          <button
            class="w-16 h-10 bg-slate-600 rounded-md text-2xl flex justify-center items-center"
            @click="incrementKey"
          >
            <icon :icon="mdiPlus" />
          </button>
        </div>
      </div>
      <div class="flex items-center justify-between grow-0 h-1/4 px-3">
        <img src="/ember.png" class="h-24" />
        <div class="flex gap-1 items-center">
          <button
            class="w-16 h-10 bg-slate-600 rounded-md text-2xl flex justify-center items-center"
            @click="decrementEmbers"
          >
            <icon :icon="mdiMinus" />
          </button>
          <div class="text-5xl w-20 text-center" style="font-family: 'Bungee Spice', sans-serif">
            {{ embers }}
          </div>
          <button
            class="w-16 h-10 bg-slate-600 rounded-md text-2xl flex justify-center items-center"
            @click="incrementEmbers"
          >
            <icon :icon="mdiPlus" />
          </button>
          <button
            class="w-32 h-10 bg-slate-600 rounded-md text-2xl tracking-wider"
            @click="forgeKey"
          >
            FORGE
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, reactive } from 'vue';
import { Player } from '../types/Player';
import { mdiPlus, mdiMinus } from '@mdi/js';
import Icon from './Icon.vue';

const props = defineProps<{
  player: Player;
}>();

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

const forgeKey = () => {
  if (embers.value >= 6) {
    incrementKey();
    embers.value -= 6;
  }
};

const embers = ref(0);

const incrementEmbers = () => {
  embers.value++;
};

const decrementEmbers = () => {
  if (embers.value > 0) {
    embers.value--;
  }
};
</script>

<style scoped></style>
