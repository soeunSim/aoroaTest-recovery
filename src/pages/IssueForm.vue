<template>
  <div>
    <IssueFormInner @goBack="goToBack"></IssueFormInner>
  </div>
</template>

<script setup>
import IssueFormInner from '../components/issue/IssueFormInner.vue'
import { useRouter } from 'vue-router'

const router = useRouter()
function goToBack() {
  router.push('/')
}
</script>
