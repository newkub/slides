<script setup lang="ts">
defineProps<{
  title?: string
  filename?: string
  lang?: string
}>()
</script>

<template>
  <div class="code-block-wrapper">
    <div v-if="filename" class="code-block-filename">{{ filename }}</div>
    <slot />
  </div>
</template>

<style scoped>
.code-block-wrapper {
  border-radius: 8px;
  overflow: hidden;
}
.code-block-filename {
  font-size: 0.75rem;
  opacity: 0.6;
  margin-bottom: 0.25rem;
}
</style>
