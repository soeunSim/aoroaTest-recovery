<template>
  <div class="card">
    <IssueFormInner
      :formData="formData"
      :selectUsers="props.selectUsers"
      @saveData="(data) => emit('saveData', data)"
      @goBack="$emit('goBack')"
    ></IssueFormInner>
  </div>
</template>

<script setup>
import IssueFormInner from '../components/issue/IssueFormInner.vue'
import { reactive, computed } from 'vue'
import { useRoute } from 'vue-router'

const props = defineProps({
  issueList: Array,
  selectUsers: Array,
})

const emit = defineEmits(['saveData', 'goBack'])

const route = useRoute()
const issueId = route.params.id
const isEditMode = !!issueId

const currentIssue = computed(() => {
  return props.issueList?.find((issue) => issue.id === Number(issueId))
})

const baseForm = () => ({
  title: '',
  description: '',
  status: 'PENDING',
  userId: '',
  user: null,
  createdAt: '',
  updatedAt: '',
})

const formData = reactive(
  isEditMode && currentIssue.value
    ? { ...currentIssue.value, userId: currentIssue.value.user?.id || '' }
    : baseForm(),
)
</script>
