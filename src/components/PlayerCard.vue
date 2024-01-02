<template>
  <div class="h-1/2 w-1/3 p-2">
    <div
      class="flex flex-col w-full h-full bg-slate-500 rounded-xl overflow-hidden justify-start"
    >
      <div class="grow-0 py-3 text-slate-100 text-4xl uppercase tracking-wider">
        <h3 class="text-center text-shadow text-amber-600">
          {{ player.name }}
        </h3>
      </div>
      <div class="flex items-center justify-between grow-0 h-1/4 px-3">
        <img :src="keyArray[keyIndex]" class="h-24" />
        <div class="flex gap-1">
          <kf-button @click="decrementKey">
            <icon size="34" :icon="mdiMinus" />
          </kf-button>
          <kf-button @click="incrementKey">
            <icon size="34" :icon="mdiPlus" />
          </kf-button>
        </div>
      </div>
      <div class="flex items-center justify-between grow-0 h-1/4 px-3">
        <img src="/ember.png" class="h-24" />
        <div class="flex gap-1 items-center">
          <kf-button @click="decrementEmbers">
            <icon size="34" :icon="mdiMinus" />
          </kf-button>
          <div class="text-5xl w-20 text-center text-shadow text-amber-600">
            {{ embers }}
          </div>
          <kf-button @click="incrementEmbers">
            <icon size="34" :icon="mdiPlus" />
          </kf-button>
          <kf-button @click="forgeKey"> FORGE </kf-button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, reactive } from "vue";
import { Player } from "../types/Player";
import { mdiPlus, mdiMinus } from "@mdi/js";
import Icon from "./Icon.vue";
import KfButton from "./KfButton.vue";

const props = defineProps<{
  player: Player;
}>();

const keyIndex = ref(0);
const keyArray = reactive([
  "/keyempty.png",
  "/key1.png",
  "/key2.png",
  "/keyfull.png",
]);

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
