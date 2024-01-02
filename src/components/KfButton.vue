<template>
  <div
    class="text-2xl bg-amber-500 text-amber-700 text-shadow text-center inline-block m-1 font-bold py-3 px-3 cursor-pointer btn-box-shadow shadow-amber-600 active:shadow-none active:relative active:top-1 rounded-lg uppercase"
    @click="clickHandler"
  >
    <slot />
  </div>
</template>

<script setup lang="ts">
const emits = defineEmits(["click"]);

const clickHandler = () => {
  emits("click");
};
</script>

<style scoped></style>
