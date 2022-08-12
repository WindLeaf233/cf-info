<template>
  <Suspense>
    <template #default>
      <InfoTable></InfoTable>
    </template>
    <template #fallback>
      Loading...
    </template>
  </Suspense>
</template>

<script setup>
import { defineAsyncComponent } from 'vue'

const InfoTable = defineAsyncComponent(() => import('@/components/InfoTable'))
</script>
