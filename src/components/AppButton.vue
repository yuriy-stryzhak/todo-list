<template>
  <button
    class="app-button"
    :class="{
      'w-full': fullWidth
    }"
    :title="title"
  >
    <slot />
  </button>
</template>
<script lang="ts">
import { defineComponent } from 'vue'
export default defineComponent({
  name: 'AppButton',
  props: {
    title: { type: String },
    fullWidth: { type: Boolean, default: false }
  }
})
</script>
<style>
button {
  border: none;
  outline: none;
  background: none;
  cursor: pointer;
}

button:focus {
  outline: 0;
}
</style>
