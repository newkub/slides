<script setup lang="ts">
defineProps<{
  title?: string
}>()
</script>

<template>
  <div class="center-layout">
    <div class="content">
      <slot />
    </div>
  </div>
</template>

<style scoped>
.center-layout {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}
.content {
  text-align: center;
}
</style>
