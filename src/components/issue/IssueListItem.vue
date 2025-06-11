<template>
  <li class="issue-list-item">
    <span class="issue-status">{{ props.issue.status }}</span>
    <p class="issue-title">{{ props.issue.title }}</p>
    <div>
      <span class="issue-manager">{{ issue.user ? issue.user.name : '미지정' }}</span> |
      <span class="issue-date">{{ props.issue.createdAt }}</span>
    </div>
  </li>
</template>

<script setup>
const props = defineProps({
  issue: Object,
})
</script>
