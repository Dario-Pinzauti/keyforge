<template>

  <div
   :class="!disable ? classEnable : classDisable"
  >
  <div class="px-2   py-2 hover:bg-amber-600 rounded-t-md" @click="clickPlusHandler">+</div>
  <div class="px-2 py-1 hover:bg-amber-600 rounded-b-md" @click="clickMinusHandler">-</div>
  </div>

</template>

<script setup lang="ts">
import { defineProps, defineEmits, ref } from "vue";

const emits = defineEmits(["clickPlus", "clickMinus"]);
const props = defineProps({
  disable: Boolean,
});

// :class="!disable ? classEnable : classDisable"

const classEnable = ref(` text-sm bg-amber-500 text-amber-700 text-shadow text-center inline-block m-1 font-bold  cursor-pointer btn-box-shadow shadow-amber-600 active:shadow-none active:relative active:top-1 rounded-lg uppercase`);

const classDisable = ref(` text-sm bg-gray-500 text-gray-700 text-shadow text-center inline-block m-1 font-bold  cursor-pointer btn-box-shadow shadow-gray-600 active:shadow-none active:relative active:top-1 rounded-lg uppercase`);


const clickPlusHandler = () => {
  emits("clickPlus");
};


const clickMinusHandler = () => {
  emits("clickMinus");
};
</script>

<style scoped></style>
