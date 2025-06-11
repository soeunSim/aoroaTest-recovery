<template>
  <div class="card">
    <h1>이슈 리스트</h1>
    <IssueStatusFilter :STATUS_OPTIONS="STATUS_OPTIONS" v-model="selected" />
    <ul>
      <IssueListItem v-for="issue in props.issueList" :key="issue.id" :issue="issue" />
    </ul>
    <div class="card-bottom">
      <BaseButton @click="goToNewIssue" buttonName="신규 이슈 등록" variant="primary" />
    </div>
  </div>
</template>

<script setup>
import { STATUS_OPTIONS } from '../constants/statusOptions.js'
import IssueStatusFilter from '../components/issue/IssueStatusFilter.vue'
import IssueListItem from '../components/issue/IssueListItem.vue'
import BaseButton from '../components/base/BaseButton.vue'
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const props = defineProps({
  issueList: Array,
})

const selected = ref('')

const router = useRouter()
function goToNewIssue() {
  router.push('issues/new')
}
</script>
