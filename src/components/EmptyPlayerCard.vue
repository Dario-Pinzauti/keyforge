<template>
  <div class="h-1/2 w-1/3 p-2">
    <div
      class="flex w-full h-full justify-center items-center bg-slate-500 hover:bg-slate-400 rounded-xl overflow-hidden text-8xl cursor-pointer"
    >
      <icon :icon="mdiPlus" size="96" />
    </div>
  </div>
</template>

<script setup lang="ts">
import Icon from './Icon.vue';
import { mdiPlus } from '@mdi/js';
</script>

<style scoped></style>
