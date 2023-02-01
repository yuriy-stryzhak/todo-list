<template>
  <component :is="tag" class="app-heading__title" :class="appearance && [`m-${appearance}`]">
    <!--@slot Heading title.-->
    <slot />
  </component>
</template>
<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'AppHeading',
  props: {
    /**
     * HTML tag
     * The h1 to h6 HTML elements represent six levels of section headings.
     * @values h1, h2, h3, h4, h5, h6
     */
    tag: { type: String, default: 'h1' },

    /**
     * UI representation of the Heading
     * @values h1, h2, h3, h4, h5, h6
     */
    appearance: { type: String, default: '' }
  }
})
</script>

<style scoped>
h1 {
  font-weight: bold;
  font-size: 2.06rem;
  line-height: 42px;
  margin-bottom: 8px;
  padding: 0 60px;
  margin: 0;
}
</style>
