<template>
  <div class="row">
    <div v-for="column in props.list" :key="column.id" class="col-4 mb-4">
      <div class="card h-100 shadow-sm">
        <div class="card-body text-center">
          <img :src="column.avatar" :alt="column.title" class="round-circle border border-light w-25 my-3" />
          <h5 class="card-title">{{ column.title }}</h5>
          <p class="card-text text-left">{{ column.description }}</p>
          <a href="#" class="btn btn-outline-primary">进入专栏</a>
        </div>
      </div>
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

const props = defineProps<Props>()
</script>