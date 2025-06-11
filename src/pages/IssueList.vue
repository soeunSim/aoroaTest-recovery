<template>
  <div>
    <h1>이슈 리스트</h1>
    <ul>
      <IssueListItem v-for="issue in issues" :key="issue.id" :issue="issue" />
    </ul>
    <div>
      <BaseButton @click="goToNewIssue" buttonName="신규 이슈 등록" variant="primary" />
    </div>
  </div>
</template>

<script setup>
import IssueListItem from '../components/issue/IssueListItem.vue'
import { issues as issueMockListData } from '../data/mockData.js'
import BaseButton from '../components/base/BaseButton.vue'
import { useRouter } from 'vue-router'
import { reactive } from 'vue'

const issues = reactive(issueMockListData)

const router = useRouter()
function goToNewIssue() {
  router.push('issues/new')
}
</script>
