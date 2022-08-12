<template>
  <el-table :data="data" style="width: 100%" :default-sort="{ prop: 'time', order: 'descending' }">
    <el-table-column prop="line" label="节点" sortable></el-table-column>
    <el-table-column prop="ip" label="IP 地址" sortable></el-table-column>
    <el-table-column prop="latency" label="平均延迟" sortable :formatter="formatterLatency"></el-table-column>
    <el-table-column prop="loss" label="丢包率" sortable :formatter="formatterLoss"></el-table-column>
    <el-table-column prop="speed" label="下载速度" sortable :formatter="formatterSpeed"></el-table-column>
    <el-table-column prop="colo" label="机房" sortable></el-table-column>
    <el-table-column prop="sptname" label="测速节点" sortable></el-table-column>
    <el-table-column prop="time" label="时间" sortable></el-table-column>
  </el-table>
</template>

<script setup>
import axios from 'axios'
import { ElNotification } from 'element-plus'
import { defineProps } from 'vue'

const props = defineProps([
    'loadingInstance'
])

const formatterLatency = (row) => `${row.latency}ms`
const formatterLoss = (row) => `${row.loss}%`
const formatterSpeed = (row) => `${row.speed}MB/s`

const getData = async function() {
  return new Promise((resolve) =>
    axios.get(process.env.VUE_APP_API).then((res) => resolve(res.data.data.server)).catch((err) => {
      console.log(err)
      ElNotification({
        title: '发生了错误',
        message: err.toString(),
        type: 'error'
      })
    }))
}

let data = await getData()
props.loadingInstance.close()
</script>
