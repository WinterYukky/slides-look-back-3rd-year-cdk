<template>
  <li>
    <slot></slot>
  </li>
</template>

<script setup lang="ts">
import { computed } from "vue";

const props = defineProps<{
  icon: string;
}>();
const listStyle = computed(() => (props.icon ? "none" : "square"));
const icon = computed(() => `"${props.icon ?? ""}"`);
</script>

<style scoped>
li {
  list-style-type: v-bind(listStyle) !important;
}
li:before {
  content: v-bind(icon);
}
</style>
