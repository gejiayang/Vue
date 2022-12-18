<template>
  <div class="columns-3">
    <div v-for="column in props.list" :key="column.id">
      <img :src="column.avatar" :alt="column.title">
      <h5>{{ column.title }}</h5>
      <p>{{ column.description }}</p>
      <a href="#">进入专栏</a>
    </div>
  </div>
</template>

<script setup lang="ts">
export interface ColumnProps {
  id: number;
  title: string;
  avatar: string;
  description: string;
}

interface Props {
  list: ColumnProps[];
}

const props = defineProps<Props>();

</script>