<template>
  <svg-icon type="mdi" :path="mdiMinus" :size="props.size" />
</template>

<script setup lang="ts">
import SvgIcon from '@jamescoyle/vue-icon';
import { mdiMinus } from '@mdi/js';

const props = withDefaults(
  defineProps<{
    size: string;
  }>(),
  {
    size: '24',
  },
);
</script>

<style scoped></style>
