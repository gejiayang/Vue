<template>
  <div class="validate-input-container pb-3">
    <input
      type="text"
      class="form-control"
      :class="{'is-invalid': inputRef.error}"
      v-model="inputRef.val"
      @blur="validateInput"
    >
    <span v-if="inputRef.error" class="invalid-feedback">{{ inputRef.message }}</span>
  </div>
</template>

<script setup lang="ts">
import { reactive } from 'vue'

export interface RuleProp {
  type: 'required' | 'email';
  message: string;
}

type RulesProp = RuleProp[]

interface Props {
  rules: RulesProp
}

const props = defineProps<Props>()

const emailReg = /^\w+([-+.]\w+)*@\w+([-.]\w+)*\.\w+([-.]\w+)*$/

const inputRef = reactive({
  val: '',
  error: false,
  message: ''
})

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