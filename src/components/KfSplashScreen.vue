<template>
  <div
    class="h-screen w-screen overflow-hidden flex justify-center items-center bg-slate-800 relative"
  >
    <span
      class="uppercase text-2xl absolute top-24 opacity-0 transition-all duration-3000 text-amber-600"
      :class="{ 'opacity-100 text-7xl': initialTransition }"
    >
      chiava la forgia
    </span>
    <KfButton @click="startClickHandler"> START </KfButton>
  </div>
</template>

<script setup lang="ts">
import { onMounted, ref, onRenderTracked } from "vue";
import KfButton from "./KfButton.vue";

const initialTransition = ref(false);

onRenderTracked(() => {
  initialTransition.value = true;
});

const startClickHandler = () => {
  console.log("sadosadk");
};
</script>

<style scoped></style>
