<template>
  <form class="validate-form-container">
    <slot name="default"></slot>
    <div class="submit-area">
      <slot name="submit">
        <button type="submit" class="btn btn-primary">提交</button>
      </slot>
    </div>
  </form>
</template>