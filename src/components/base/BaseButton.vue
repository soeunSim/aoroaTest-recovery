<template>
  <button :class="['btn', variant]" @click="handleClick">
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

const emit = defineEmits(['click'])

function handleClick(event) {
  emit('click', event)
}
</script>
