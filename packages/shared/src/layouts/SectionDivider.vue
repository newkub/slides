<script setup lang="ts">
defineProps<{
  title?: string
}>()
</script>

<template>
  <div class="section-divider">
    <h1 v-if="title">{{ title }}</h1>
    <slot />
  </div>
</template>

<style scoped>
.section-divider {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100%;
}
</style>
