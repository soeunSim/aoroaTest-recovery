<template>
  <div>
    <IssueFormInner
      :formData="formData"
      :selectUsers="selectUsers"
      @saveData="(data) => emit('saveData', data)"
      @goBack="goToBack"
    ></IssueFormInner>
  </div>
</template>

<script setup>
import IssueFormInner from '../components/issue/IssueFormInner.vue'
import { reactive } from 'vue'

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
