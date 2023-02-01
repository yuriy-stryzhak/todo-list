<template>
  <input
    class="set__control set__input"
    :type="type"
    :maxlength="maxlength"
    :minlength="minlength"
    :placeholder="placeholder"
    :value="value"
  />
</template>
<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'AppInput',
  props: {
    /** Form input maxlength attr */
    maxlength: { type: Number, default: 255 },
    /** Form input minlength attr */
    minlength: { type: Number },
    /** A string that provides a brief hint to the user */
    placeholder: { type: String, default: '' },
    type: { type: String, default: 'text' },
    value: { type: String, default: '' }
  },
  setup() {
    return {}
  }
})
</script>

<style>
.set__control {
  border-radius: var(--radius);
  border: none;
  font-family: Trebuchet, Arial, sans-serif;
  outline: none;
  padding: 10px 15px;
  min-height: 50px;
  font-size: 16px;
  display: inline-block;
  box-sizing: border-box;
  background-color: #fff;
  transition: all 0.25s;
}

.set__control::placeholder {
  opacity: 0.5;
  transition: all 0.25s;
}

.set__control:focus::placeholder {
  opacity: 0;
}

.set__input {
  flex-grow: 1;
  color: rgba(0, 0, 0, 0.7);
  border: 1px solid transparent;
}

.set__input.error {
  border-color: var(--coral);
}

.set__input.error::placeholder {
  color: var(--coral);
  opacity: 1;
}

.set__input.error:focus::placeholder {
  opacity: 0;
}
</style>
