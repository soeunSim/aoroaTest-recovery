<template>
  <div id="app">
    <router-view
      :issueList="issueList"
      :selectUsers="selectUsers"
      @saveData="handleSaveData"
      @goBack="handleGoToBack"
    />
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'
import { users, issues } from './data/mockData'
import { useRouter } from 'vue-router'

const issueList = ref([...issues])
const selectUsers = reactive([...users])

function handleSaveData(saveData) {
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
  handleGoToBack()
}

const router = useRouter()
function handleGoToBack() {
  router.push('/')
}
</script>

<style scoped></style>
