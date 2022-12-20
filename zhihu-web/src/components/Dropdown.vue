<template>
  <div class="dropdown" ref="dropdownRef">
    <a href="#" class="btn btn-outline-light my-2 dropdown-toggle" @click.prevent="toggleOpen">{{ props.title }}</a>
    <ul class="dropdown-menu" :style="{display: 'block'}" v-if="isOpen">
      <slot></slot>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { ref, watch } from 'vue'
import useClickOutside from '../hooks/useClickOutside'

interface Props {
  title: string;
}

const props = defineProps<Props>()
const isOpen = ref(false)
const dropdownRef = ref<HTMLElement | null>(null)

const isClickOutside = useClickOutside(dropdownRef)

watch(isClickOutside, () => {
  if (isClickOutside.value && isOpen.value) {
    isOpen.value = false
  }
})

const toggleOpen = () => {
  isOpen.value = !isOpen.value
}
</script>