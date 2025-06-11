<template>
  <div>
    <h1>이슈 리스트</h1>
    <ul v-for="issue in issues" :key="issue.id">
      <IssueListItem :issue="issue" />
    </ul>
  </div>
</template>

<script setup>
import IssueListItem from '../components/issue/IssueListItem.vue'
import { issues as issueMockListData } from '../data/mockData.js'
import { reactive } from 'vue'

const issues = reactive(issueMockListData)
</script>
