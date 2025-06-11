<template>
  <div>
    <IssueFormInner
      :formData="formData"
      :selectUsers="selectUsers"
      @saveData="hendleSaveData"
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
  createdAt: '',
  updatedAt: '',
})

const selectUsers = reactive(users)

const issueList = ref(issues)
function hendleSaveData(saveData) {
  if (!saveData.title || !saveData.description) {
    alert('입력칸을 채워주세요.')
    return
  }
  if (!saveData.userId) {
    saveData.status = 'PENDING'
  }
  saveData.createdAt = new Date().toISOString()
  saveData.updatedAt = new Date().toISOString()
  saveData.user = selectUsers.find((user) => user.id === Number(saveData.userId)) || null

  issueList.value.push({ ...saveData })
  goToBack()
}

const router = useRouter()
function goToBack() {
  router.push('/')
}
</script>
