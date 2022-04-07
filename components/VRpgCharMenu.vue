<template>
  <v-rpg-panel class="grid text-center divide-y-2">
    <div class="py-2" style="border-top: 0"><slot name="name"></slot></div>
    <slot>
      <div class="grid grid-cols-2">
        <li>こうげき</li>
        <li>どうぐ</li>
        <li>じゅもん</li>
        <li>そうび</li>
        <li>ぼうぎょ</li>
        <li>にげる</li>
      </div>
    </slot>
  </v-rpg-panel>
</template>

<style scoped>
li {
  font-size: 1rem !important;
  list-style-type: none;
}
li:hover {
  list-style-type: "▶";
  margin-left: 0;
  cursor: pointer;
}
</style>
