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

<style scoped>
li.issue-list-item {
  list-style: none;
  cursor: pointer;
}
li.issue-list-item .issue-title {
  width: 250px;
  text-overflow: ellipsis;
  white-space: nowrap;
  overflow: hidden;
}
li.issue-list-item .issue-status {
  display: inline-block;
  padding: 0px 4px;
  border: 1px solid #888888;
  color: #888888;
  border-radius: 2px;
  min-width: 80px;
  text-align: center;
  margin-right: 10px;
}
</style>
