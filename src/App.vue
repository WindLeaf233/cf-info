<template>
  <div class="common-layout">
    <el-container>
      <el-header class="header">
        <strong class="title">cf-info</strong>
      </el-header>
      <el-container>
        <el-aside :width="asideWidth + 'px'"></el-aside>
        <el-main>
          <Suspense>
            <template #default>
              <InfoTable :loadingInstance="loadingInstance"></InfoTable>
            </template>
            <template #fallback></template>
          </Suspense>
        </el-main>
        <el-aside :width="asideWidth + 'px'"></el-aside>
      </el-container>
    </el-container>
  </div>
</template>

<script setup>
import { defineAsyncComponent } from 'vue'
import { ElLoading } from 'element-plus'

const asideWidth = '150'
const loadingInstance = ElLoading.service({ fullscreen: true, lock: true })

const InfoTable = defineAsyncComponent(() => import('@/components/InfoTable'))
</script>

<style scoped>
.header {
  margin: auto;
  padding: 3% 3% 5%;
}

.title {
  font-size: 30px;
  margin: auto;
}
</style>
