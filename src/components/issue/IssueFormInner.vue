<template>
  <form>
    <div>
      <div>
        <label for="">제목</label>
        <input id="" />
      </div>
      <div>
        <label for="">설명</label>
        <textarea id="" />
      </div>
      <div>
        <label for="">담당자</label>
        <select id="">
          <option></option>
        </select>
      </div>
      <div>
        <label for="">상태</label>
        <select id="">
          <option></option>
        </select>
      </div>
      <div>
        <BaseButton buttonName="저장"></BaseButton>
        <BaseButton buttonName="목록 보기" variant="ghost"></BaseButton>
      </div>
    </div>
  </form>
</template>

<script setup>
import BaseButton from '../base/BaseButton.vue'
</script>

<style scoped></style>
