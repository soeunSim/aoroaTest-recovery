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

  const existingIndex = issueList.value.findIndex((issue) => issue.id === saveData.id)

  const matchedUser = selectUsers.find((user) => user.id === Number(saveData.userId)) || null
  saveData.user = matchedUser

  const now = new Date().toISOString()

  if (existingIndex !== -1) {
    issueList.value[existingIndex] = {
      ...issueList.value[existingIndex],
      ...saveData,
      updatedAt: now,
    }
  } else {
    issueList.value.push({
      ...saveData,
      id: Date.now(),
      createdAt: now,
      updatedAt: now,
    })
  }

  handleGoToBack()
}

const router = useRouter()
function handleGoToBack() {
  router.push('/')
}
</script>

<style scoped></style>
