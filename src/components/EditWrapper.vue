<template>
  <div class="edit-wrapper" :class="{active: isActive}" @click="onItemClick">
    <slot></slot>
  </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'edit-wrapper',
  props: {
    id: {
      type: String,
      required: true
    },
    isActive: {
      type: Boolean,
      default: false
    }
  },
  emits: ['set-active'],
  setup(props, context) {
    const onItemClick = () => {
      context.emit('set-active', props.id)
    }
    return {
      onItemClick
    }
  }
})
</script>
<style scoped>
  .active {
    border: 1px dashed red;
  }
</style>