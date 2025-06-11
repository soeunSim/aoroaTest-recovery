<template>
  <li class="issue-list-item">
    <span class="issue-status">상태</span>
    <p class="issue-title">제목이 들어갈 자리 입니다.</p>
    <div>
      <span class="issue-manager">담당자</span> |
      <span class="issue-date">생성일</span>
    </div>
  </li>
</template>

<script setup></script>

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
