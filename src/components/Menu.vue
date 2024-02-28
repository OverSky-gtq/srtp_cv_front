<template>
  <el-menu :default-active="activeIndex" class="el-menu-demo" mode="horizontal" :ellipsis="false" @select="handleSelect">
    <el-menu-item index="0">
      <img style="width: 55px" src="/src/assets/seu.png" alt="Seu logo" />
    </el-menu-item>
    <div class="flex-grow" />
    <el-menu-item index="1">主页</el-menu-item>
    <el-sub-menu index="2">
      <template #title>功能</template>
      <el-menu-item index="2-1">1</el-menu-item>
      <el-menu-item index="2-2">2</el-menu-item>
      <el-menu-item index="2-3">3</el-menu-item>
      <el-sub-menu index="2-4">
        <template #title>4</template>
        <el-menu-item index="2-4-1">4-1</el-menu-item>
        <el-menu-item index="2-4-2">4-2</el-menu-item>
        <el-menu-item index="2-4-3">4-3</el-menu-item>
      </el-sub-menu>
    </el-sub-menu>
  </el-menu>
</template>
  
<script lang="ts" setup>
import { ref } from 'vue'

const activeIndex = ref('1')
const handleSelect = (key: string, keyPath: string[]) => {
  console.log(key, keyPath)
}
</script>
  
<style>
.flex-grow {
  flex-grow: 1;
}

.el-menu-demo {
  background-color: rgb(246, 246, 246);
}
</style>
  