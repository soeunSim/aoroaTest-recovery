<template>
  <form @submit.prevent>
    <div>
      <div>
        <label for="formTitle">제목</label>
        <input id="formTitle" v-model="localForm.title" />
      </div>
      <div>
        <label for="formDescription">설명</label>
        <textarea id="formDescription" v-model="localForm.description" />
      </div>
      <div>
        <label for="formUser">담당자</label>
        <select id="formUser" v-model="localForm.userId">
          <option disabled value="">담당자 선택</option>
          <option v-for="user in props.selectUsers" :key="user.id" :value="user.id">
            {{ user.name }}
          </option>
        </select>
      </div>
      <div>
        <label for="formStatus">상태</label>
        <select id="formStatus" v-model="localForm.status">
          <option disabled value="">상태 선택</option>
          <option value="PENDING">PENDING</option>
          <option value="IN_PROGRESS">IN_PROGRESS</option>
          <option value="COMPLETED">COMPLETED</option>
          <option value="CANCELLED">CANCELLED</option>
        </select>
      </div>
      <div>
        <BaseButton
          buttonName="저장"
          type="submit"
          @click="emit('saveData', localForm)"
        ></BaseButton>
        <BaseButton buttonName="목록 보기" variant="ghost" @click="emit('goBack')"></BaseButton>
      </div>
    </div>
  </form>
</template>

<script setup>
import BaseButton from '../base/BaseButton.vue'
import { reactive } from 'vue'

const props = defineProps({
  formData: Object,
  selectUsers: Object,
})

const emit = defineEmits(['goBack', 'saveData'])

const localForm = reactive({ ...props.formData })
</script>

<style scoped></style>
