<template>
  <div>
    <IssueFormInner
      :formData="formData"
      :selectUsers="props.selectUsers"
      @saveData="(data) => emit('saveData', data)"
      @goBack="goToBack"
    ></IssueFormInner>
  </div>
</template>

<script setup>
import IssueFormInner from '../components/issue/IssueFormInner.vue'
import { reactive } from 'vue'

const props = defineProps({
  selectUsers: Array,
})

const emit = defineEmits(['saveData'])

const formData = reactive({
  title: '',
  description: '',
  status: 'PENDING',
  userId: '',
  user: null,
  createdAt: '',
  updatedAt: '',
})
</script>
