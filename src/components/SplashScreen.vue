<template>
  <div
    class="h-screen w-screen box-border m-0 overflow-hidden flex flex-col justify-center items-center bg-slate-500 transition-all duration-3000"
    :class="showSplashScreen ? 'opacity-100' : 'opacity-0'"
  >
    <div class="flex justify-center items-center relative">
      <icon
        :icon="mdiHammerSickle"
        size="960"
        class="text-slate-700 absolute z-0"
      />
      <icon :icon="mdiKey" size="768" class="text-slate-400 absolute z-10" />
    </div>
    <div class="z-20">
      <h1
        class="text-9xl"
        style="font-family: &quot;Bungee Spice&quot;, sans-serif"
      >
        Forgia ì chiavo
      </h1>
    </div>
  </div>
</template>

<script setup lang="ts">
import { onMounted, ref } from "vue";
import Icon from "./Icon.vue";

import { mdiHammerSickle, mdiKey } from "@mdi/js";

const showSplashScreen = ref(true);

onMounted(() => {
  setTimeout(() => {
    showSplashScreen.value = false;
  }, 2000);
});
</script>

<style scoped></style>
