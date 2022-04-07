<template>
  <v-fall
    v-for="fall in falls"
    :key="fall.id"
    :x="fall.x"
    :y="fall.y"
    :rotate="fall.rotate"
    :scale="fall.scale"
    :speed="props.speed"
    v-bind="$attrs"
  >
    <slot></slot>
  </v-fall>
</template>

<script setup lang="ts">
import { ref, watch } from "vue";
const props = defineProps<{
  speed: number;
  interval: number;
  max: number;
}>();
interface FallText {
  id: string;
  x: number;
  y: number;
  rotate: number;
  scale: number;
}
const falls = ref<FallText[]>([]);
const generateInterval = () =>
  setInterval(() => {
    falls.value.push({
      id: new Date().getTime().toString(),
      x: Math.round(Math.random() * 980) - 50,
      y: -Math.round(Math.random() * 100) - 100,
      rotate: Math.round(Math.random() * 360),
      scale: -1,
    });
  }, props.interval);
setInterval(() => {
  if (falls.value.length > props.max) {
    for (; falls.value.length > props.max; ) {
      falls.value.shift();
    }
  }
}, 10);
const interval = ref(generateInterval());
watch(
  () => props.interval,
  () => {
    clearInterval(interval.value);
    interval.value = generateInterval();
  }
);
</script>
