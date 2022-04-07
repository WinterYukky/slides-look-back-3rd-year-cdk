<template>
  <div
    v-for="onomatopoeia in onomatopoeias"
    :key="onomatopoeia.createdAt.toISOString()"
    class="transform text-3xl"
    style="position: absolute"
    :style="[
      `transform: rotate(${onomatopoeia.angle}deg)`,
      `top: ${y + onomatopoeia.distance.y}px;`,
      `left: ${x + onomatopoeia.distance.x}px;`,
    ]"
    v-bind="$attrs"
  >
    <div v-motion-fade :enter="{ opacity: 0.7 }">{{ text }}</div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
const props = defineProps<{
  text: string;
  max: number;
  x: number;
  y: number;
}>();
interface Onomatopoeia {
  angle: number;
  distance: {
    x: number;
    y: number;
  };
  createdAt: Date;
}
const onomatopoeias = ref<Onomatopoeia[]>([]);
setInterval(() => {
  if (onomatopoeias.value.length > props.max) {
    onomatopoeias.value.shift();
  }
  if (
    onomatopoeias.value.length === 0 ||
    onomatopoeias.value[onomatopoeias.value.length - 1].createdAt.getTime() +
      1000 <
      new Date().getTime()
  ) {
    const xFlip = Math.random() < 0.5;
    const yFlip = Math.random() < 0.5;
    const angle = Math.round(Math.random() * 30) + (xFlip ? 330 : 0);
    const onomatopoeia: Onomatopoeia = {
      angle,
      distance: {
        x: Math.round(Math.round(Math.random() * 50) + 15) * (xFlip ? -1 : 1),
        y: Math.round(Math.round(Math.random() * 30) + 13) * (yFlip ? -1 : 1),
      },
      createdAt: new Date(),
    };
    onomatopoeias.value.push(onomatopoeia);
  }
}, 10);
</script>
