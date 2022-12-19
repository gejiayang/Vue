<script setup lang="ts">
import GlobalHeader, { type UserProps } from './components/GlobalHeader.vue'
import ColumnList, { type ColumnProps } from './components/ColumnList.vue'

const currentUser: UserProps = {
  isLogin: true,
  id: 1,
  name: 'Oliver'
}

const testData: ColumnProps[] = [
  {
    id: 1,
    title: '标题1',
    description: '描述1',
    avatar: 'https://picx.zhimg.com/80/v2-965a81075317d91f55cda3652859f3bb_1440w.webp?source=1940ef5c'
  },
  {
    id: 2,
    title: '标题2',
    description: '描述2',
    avatar: 'https://picx.zhimg.com/80/v2-965a81075317d91f55cda3652859f3bb_1440w.webp?source=1940ef5c'
  },
  {
    id: 3,
    title: '标题3',
    description: '描述3',
    avatar: 'https://picx.zhimg.com/80/v2-965a81075317d91f55cda3652859f3bb_1440w.webp?source=1940ef5c'
  },
  {
    id: 4,
    title: '标题4',
    description: '描述4',
    avatar: 'https://picx.zhimg.com/80/v2-965a81075317d91f55cda3652859f3bb_1440w.webp?source=1940ef5c'
  }
]
</script>

<template>
  <div class="container">
    <GlobalHeader :user="currentUser" />
    <ColumnList :list="testData" />
  </div>
</template>

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
