<template>
  <h1>アジェンダ</h1>
  <div class="grid items-center h-4/5">
    <ul>
      <li
        v-for="(agenda, i) in agendas"
        :class="{
          'opacity-90': !step || step === i + 1,
          'opacity-50': step && step !== i + 1,
        }"
      >
        {{ agenda }}
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
defineProps<{
  step?: number;
}>();

const agendas = ref([
  "私が初学者にCDKをオススメする理由",
  "これまでの運用における成功と失敗",
  '"Pre" カンファレンスで頂いた質問',
]);
</script>

<style scoped>
li {
  font-size: 1.8rem !important;
}
</style>
