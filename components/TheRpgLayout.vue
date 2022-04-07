<template>
  <div class="w-2/5">
    <slot name="party"></slot>
  </div>
  <div class="h-1/2 grid items-center justify-center">
    <slot name="enemy"></slot>
  </div>
  <div class="w-full h-2/7">
    <slot></slot>
  </div>
</template>
