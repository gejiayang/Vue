<template>
  <li class="dropdown-option" :class="{'is-disabled': props.disabled}">
    <slot></slot>
  </li>
</template>

<script setup lang="ts">
interface Props {
  disabled: boolean;
}

const props = withDefaults(defineProps<Props>(), {
  disabled: false
})
</script>

<style>
.dropdown-option.is-disabled * {
  color: #6c757d;
  pointer-events: none;
  background-color: transparent;
}
</style>
