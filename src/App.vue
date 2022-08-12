<template>
  <Suspense>
    <template #default>
      <InfoTable :loadingInstance="loadingInstance"></InfoTable>
    </template>
    <template #fallback></template>
  </Suspense>
</template>

<script setup>
import { defineAsyncComponent } from 'vue'
import { ElLoading } from 'element-plus'

const loadingInstance = ElLoading.service({ fullscreen: true, lock: true })
const InfoTable = defineAsyncComponent(() => import('@/components/InfoTable'))
</script>
