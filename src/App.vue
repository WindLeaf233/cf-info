<template>
  <div class="common-layout">
    <el-container>
      <el-header class="header">
        <strong class="title">cf-info</strong>
      </el-header>
      <el-container :class="device.mobile ? 'main-container-mobile' : 'main-container-desktop'">
        <el-main>
          <Suspense>
            <template #default>
              <div>
                <InfoTable :loadingInstance="loadingInstance"></InfoTable>
              </div>
            </template>
            <template #fallback>
              <div></div>
            </template>
          </Suspense>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script setup>
import { defineAsyncComponent } from 'vue'
import { ElLoading } from 'element-plus'
import {createDeviceDetector} from 'next-vue-device-detector'

const loadingInstance = ElLoading.service({ fullscreen: true, lock: true })
const device = createDeviceDetector()

const InfoTable = defineAsyncComponent(() => import('@/components/InfoTable'))
</script>

<style scoped>
.header {
  margin: auto;
  padding-top: 3%;
  text-align: center;
}

.title {
  font-size: 30px;
  margin: auto;
  display: inline-block;
  vertical-align: middle;
}

.main-container-desktop {
  padding: 3% 7% 7%;
}

.main-container-mobile {
  padding: 0;
  width: 100%;
}
</style>
