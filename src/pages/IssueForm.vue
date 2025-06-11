<template>
  <div>
    <IssueFormInner
      :formData="formData"
      :selectUsers="selectUsers"
      @goBack="goToBack"
    ></IssueFormInner>
  </div>
</template>

<script setup>
import IssueFormInner from '../components/issue/IssueFormInner.vue'
import { ref, reactive } from 'vue'
import { useRouter } from 'vue-router'
import { users, issues } from '../data/mockData'

const formData = reactive({
  title: '',
  description: '',
  status: 'PENDING',
  userId: '',
  user: null,
  createdAt: new Date().toISOString(),
  updatedAt: new Date().toISOString(),
})

const selectUsers = reactive(users)
const issueList = ref(issues)

const router = useRouter()
function goToBack() {
  router.push('/')
}
</script>
