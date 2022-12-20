<template>
  <div class="validate-input-container pb-3">
    <input
      v-bind="$attrs"
      class="form-control"
      :class="{'is-invalid': inputRef.error}"
      :value="inputRef.val"
      @input="updateValue"
      @blur="validateInput"
    >
    <span v-if="inputRef.error" class="invalid-feedback">{{ inputRef.message }}</span>
  </div>
</template>

<script lang="ts">
export default {
  inheritAttrs: false
};
</script>
<script setup lang="ts">
import { reactive } from 'vue'

export interface RuleProp {
  type: 'required' | 'email';
  message: string;
}

type RulesProp = RuleProp[]

interface Props {
  rules: RulesProp;
  modelValue: string;
}

const props = defineProps<Props>()
const emit = defineEmits(['update:modelValue'])

const emailReg = /^\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*$/

const inputRef = reactive({
  val: props.modelValue || '',
  error: false,
  message: ''
})

const updateValue = (e: Event) => {
  const targetValue = (e.target as HTMLInputElement).value
  inputRef.val = targetValue
  emit('update:modelValue', targetValue)
}

const validateInput = () => {
  if (props.rules) {
    const allPassed = props.rules.every(rule => {
      let passed = false
      inputRef.message = rule.message
      switch(rule.type) {
        case 'required':
          passed = inputRef.val.trim() !== ''
          break
        case 'email':
          passed = emailReg.test(inputRef.val)
          break
        default:
          break
      }
      return passed
    })
    inputRef.error = !allPassed
    return allPassed
  }
}
</script>