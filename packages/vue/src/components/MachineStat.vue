<template>
  <div v-if="value && !value.toString().includes('NaN') && !value.toString().includes('undefined')" class="flex whitespace-nowrap gap-2 max-w-64 items-center">
    <div class="flex items-center gap-2" :class="!dontFade && 'opacity-50'">
      <slot />
    </div>
    <p class="overflow-ellipsis overflow-hidden">
      {{ value }} <strong class="font-normal opacity-50">{{ suffix }}</strong>
    </p>
  </div>
  <div v-else class="flex whitespace-nowrap gap-2 items-center opacity-50">
    <slot />
    n/a
  </div>
</template>

<script setup lang="ts">
defineProps<{value?: string | number; suffix?: string; dontFade?: boolean}>();
</script>
