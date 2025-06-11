<template>
  <button :class="['btn', variant]" :type="type" @click="handleClick">
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
  type: {
    type: String,
    default: 'button',
  },
})

const emit = defineEmits(['click'])

function handleClick(event) {
  event.preventDefault()
  emit('click', event)
}
</script>
