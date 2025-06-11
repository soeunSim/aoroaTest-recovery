<template>
  <label for="statusFilter">상태 필터:</label>
  <select id="statusFilter" v-model="selected">
    <option v-for="option in props.STATUS_OPTIONS" :key="option.value" :value="option.value">
      {{ option.label }}
    </option>
  </select>
</template>

<script setup>
import { ref, watch } from 'vue'
const props = defineProps({
  modelValue: String,
  STATUS_OPTIONS: Array,
})

const emit = defineEmits(['update:modelValue'])

const selected = ref(props.modelValue)

watch(selected, (val) => emit('update:modelValue', val))
</script>
