<script setup>
import { computed, defineProps } from 'vue'
const props = defineProps({
  variant: {
    default: 'bg-[#FFA279]',
    type: String,
    validator: (value) => {
      return ['bg-[#FFA279]', 'gradient', 'outlined'].includes(value)
    },
  },
})

const bgStyles = computed(() => {
  return props.variant === 'bg-[#FFA279]'
    ? 'bg-gradient-to-r from-[#FFA279] to-[#F3743D]'
    : 'bg-[#FFA279]'
})
</script>

<template>
  <button
    class="rounded-xl py-3 px-10 text-white font-bold tracking-[-0.05] cursor-pointer"
    :class="bgStyles"
  >
    <slot></slot>
  </button>
</template>
