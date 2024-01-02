<template>
  <svg-icon type="mdi" :path="props.icon" :size="props.size" />
</template>

<script setup lang="ts">
import SvgIcon from "@jamescoyle/vue-icon";

const props = withDefaults(
  defineProps<{
    icon: string;
    size: string;
  }>(),
  { size: "24" },
);
</script>

<style scoped></style>
