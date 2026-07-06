<script setup lang="ts">
defineProps<{
  title: string
  description?: string
  icon?: string
}>()
</script>

<template>
  <div class="topic-card p-6 rounded-lg border border-gray-200 dark:border-gray-700">
    <div v-if="icon" class="text-3xl mb-2">{{ icon }}</div>
    <h3 class="text-xl font-bold">{{ title }}</h3>
    <p v-if="description" class="text-sm opacity-70 mt-2">{{ description }}</p>
    <slot />
  </div>
</template>
