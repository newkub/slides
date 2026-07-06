<script setup lang="ts">
defineProps<{
  headers: string[]
  rows: string[][]
}>()
</script>

<template>
  <table class="comparison-table">
    <thead>
      <tr>
        <th v-for="h in headers" :key="h">{{ h }}</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(row, i) in rows" :key="i">
        <td v-for="(cell, j) in row" :key="j" v-html="cell" />
      </tr>
    </tbody>
  </table>
</template>

<style scoped>
.comparison-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.875rem;
}
.comparison-table th,
.comparison-table td {
  padding: 0.5rem 1rem;
  border-bottom: 1px solid rgba(128, 128, 128, 0.2);
  text-align: left;
}
.comparison-table th {
  font-weight: bold;
  opacity: 0.8;
}
</style>
