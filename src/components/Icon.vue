<template>
  <svg-icon type="mdi" :path="props.icon" :class="`${evaluateSize()} mx-1 my-1`" />
</template>

<script setup lang="ts">
import SvgIcon from "@jamescoyle/vue-icon";

const props = defineProps({
  icon: String,
  size: {
    type: String,
    default: "sm",
    validator: (value: string) => {
      return ["xs", "sm", "md", "lg","xl"].includes(value);
  },
  },
});

function evaluateSize() {
  switch (props.size) {
    case "xs":
      return "size-3";
    case "sm":
      return "size-3.5";
    case "base":
      return "size-4";
    case "lg":
      return "size-4.5";
    case "xl":
      return "size-5";
    case "2xl":
      return "size-6";
    
  }
}

</script>

<style scoped></style>
