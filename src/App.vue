<template>
  <el-table
      :data="data"
      style="width: 100%"
      :default-sort="{ prop: 'time', order: 'descending' }"
  >
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
const formatterLatency = (row) => `${row.latency}ms`
const formatterLoss = (row) => `${row.loss}%`
const formatterSpeed = (row) => `${row.speed}MB/s`

const data = [
  {
    colo: "美国",
    ip: "104.20.117.36",
    latency: 206,
    line: "CM",
    loss: 0,
    speed: 425,
    time: "2022-08-10 21:08:49",
    sptname: "广东东苑"
  },
  {
    colo: "中国",
    ip: "114.51.41.91",
    latency: 13,
    line: "CT",
    loss: 0,
    speed: 999,
    time: "2022-08-10 23:04:12",
    sptname: "上海"
  }
];
</script>
