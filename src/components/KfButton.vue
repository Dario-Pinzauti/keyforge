<template>

  <div
   :class="!disable ? classEnable : classDisable"
    @click="clickHandler"
  >
    <slot  />
  </div>
</template>

<script setup lang="ts">
import { defineProps, defineEmits, ref } from "vue";

const emits = defineEmits(["click"]);
const props = defineProps({
  disable: Boolean,
  size: {
    type: String,
    default: "sm",
    validator: (value: string) => {
      return ["sm", "md", "lg","xl"].includes(value);
  },
  },
});

// :class="!disable ? classEnable : classDisable"

const classEnable = ref(`text-${props.size} bg-amber-500 text-amber-700 text-shadow text-center inline-block m-1 font-bold py-3 px-3 cursor-pointer btn-box-shadow shadow-amber-600 active:shadow-none active:relative active:top-1 rounded-lg uppercase`);

const classDisable = ref(`text-${props.size} bg-gray-500 text-gray-700 text-shadow text-center inline-block m-1 font-bold py-3 px-3 cursor-pointer btn-box-shadow shadow-gray-600 active:shadow-none active:relative active:top-1 rounded-lg uppercase`);


const clickHandler = () => {
  emits("click");
};
</script>

<style scoped></style>
