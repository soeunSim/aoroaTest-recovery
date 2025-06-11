<template>
  <button :class="['btn', variant]">
    {{ props.buttonName }}
  </button>
</template>

<script setup>
const props = defineProps({
  buttonName: String,
  variant: {
    type: String,
    default: 'primary',
  },
})
</script>
