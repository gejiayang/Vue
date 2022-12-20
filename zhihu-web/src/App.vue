<template>
  <div class="container">
    <GlobalHeader :user="currentUser" />
    <!-- <ColumnList :list="testData" /> -->
    <form action="">
      <div class="mb-3">
        <label class="form-label">邮箱地址</label>
        <ValidateInput
          :rules="emailRules"
          v-model="emailVal"
          placeholder="请输入邮箱地址"
          type="text"
        />
      </div>
      <div class="mb-3">
        <label class="form-label">密码</label>
        <ValidateInput
          :rules="passwordRules"
          v-model="passwordVal"
          placeholder="请输入密码"
          type="password"
        />
      </div>
    </form>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import GlobalHeader, { type UserProps } from './components/GlobalHeader.vue'
import ValidateInput, { type RuleProp } from './components/ValidateInput.vue'
// import ColumnList, { type ColumnProps } from './components/ColumnList.vue'

const currentUser: UserProps = {
  isLogin: true,
  id: 1,
  name: 'Oliver'
}

// const testData: ColumnProps[] = [
//   {
//     id: 1,
//     title: '标题1',
//     description: '描述1',
//     avatar: 'https://picx.zhimg.com/80/v2-965a81075317d91f55cda3652859f3bb_1440w.webp?source=1940ef5c'
//   },
//   {
//     id: 2,
//     title: '标题2',
//     description: '描述2',
//     avatar: 'https://picx.zhimg.com/80/v2-965a81075317d91f55cda3652859f3bb_1440w.webp?source=1940ef5c'
//   },
//   {
//     id: 3,
//     title: '标题3',
//     description: '描述3',
//     avatar: 'https://picx.zhimg.com/80/v2-965a81075317d91f55cda3652859f3bb_1440w.webp?source=1940ef5c'
//   },
//   {
//     id: 4,
//     title: '标题4',
//     description: '描述4',
//     avatar: 'https://picx.zhimg.com/80/v2-965a81075317d91f55cda3652859f3bb_1440w.webp?source=1940ef5c'
//   }
// ]

const emailVal = ref('')
const emailRules: RuleProp[] = [
  { type: 'required', message: '邮箱地址不能为空' },
  { type: 'email', message: '请输入正确的邮箱格式' }
]

const passwordVal = ref('')
const passwordRules: RuleProp[] = [
  { type: 'required', message: '密码不能为空' }
]


</script>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
