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
          <kf-button @click="decrementKey" size="2xl">
            <icon  :icon="mdiMinus" size="2xl" />
          </kf-button>
          <kf-button @click="incrementKey" size="2xl">
            <icon  :icon="mdiPlus" size="2xl" />
          </kf-button>
        </div>
      </div>
      <div class="flex items-center justify-between grow-0 h-1/4 px-3">
        <img src="/ember.png" class="h-24" />
        <div class="flex gap-1 items-center">
          <kf-button @click="decrementEmbers" size="2xl">
            <icon  :icon="mdiMinus" size="2xl" />
          </kf-button>
          <div class="text-5xl w-20 text-center text-shadow text-amber-600">
            {{ embers }}
          </div>
          <kf-button @click="incrementEmbers" size="2xl">
            <icon  :icon="mdiPlus" size="2xl" />
          </kf-button>
          <kf-button @click="forgeKey" :disable="!disableCreationButton" size="2xl"> FORGE </kf-button>
        </div>
      </div>
      <div class="flex items-end justify-end grow-0 h-1/4 ">
        <div class="flex ml-8">
          <div class="py-1 ">
              <div class=" flex text-xl w-20 text-right text-shadow text-amber-600">
              {{ contraintCards()  }}
              <icon  :icon="mdiCardsPlaying" class="size-7 pb-1 ml-4" /> 
          </div>
          <div class="flex text-xl w-20  text-shadow text-amber-600">
            {{ constraintsNumber }}
            <icon  :icon="mdiCircleOutline" class="size-6 pb-1 ml-4" /> 
          </div>
        </div>
        <div class="flex flex-col">
            <kf-button-group :disable="false" @click-plus="incrementConstraintsNumber" @click-minus="decrementConstraintsNumber"></kf-button-group>
        </div>

        </div>
        
        <div class="flex size-full"></div>

        <div class="flex gap-1 items-center">
          <kf-button @click="decrementEmbersCreationNumber" size="2xl">
            <icon  :icon="mdiMinus" size="2xl" />
          </kf-button>
          <div class="text-5xl w-20 text-center text-shadow text-amber-600">
            {{ emberCreationNumber }}
          </div>
          <kf-button @click="incrementEmbersCreationNumber" size="2xl">
            <icon  :icon="mdiPlus" size="2xl" />
          </kf-button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, reactive } from "vue";
import { Player } from "../types/Player";
import { mdiPlus, mdiMinus, mdiHandBackLeft, mdiCard, mdiCardMinus, mdiCardMinusOutline, mdiCardsPlaying, mdiCircle, mdiCircleOffOutline, mdiCircleBoxOutline, mdiCircleOutline } from "@mdi/js";
import Icon from "./Icon.vue";
import KfButton from "./KfButton.vue";
import KfButtonGroup from "./KfButtonGroup.vue";
import { defineProps, computed } from "vue";

const props = defineProps<{
  player: Player;
}>();

const disableCreationButton = computed(() => embers.value >= emberCreationNumber.value);

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

const emberCreationNumber = ref(6);


const incrementEmbersCreationNumber = () => {
    emberCreationNumber.value++;
};

const decrementEmbersCreationNumber = () => {
  if (emberCreationNumber.value > 0) {
    emberCreationNumber.value--;
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


const constraintsNumber = ref(0);


const incrementConstraintsNumber = () => {
    constraintsNumber.value++;
};

const decrementConstraintsNumber = () => {
  if (constraintsNumber.value > 0) {
    constraintsNumber.value--;
  }
};

const contraintCards = () => {
  return - Math.floor(constraintsNumber.value / 6 );
};

</script>

<style scoped></style>
