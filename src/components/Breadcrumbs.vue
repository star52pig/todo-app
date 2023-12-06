<template>
  <el-breadcrumb separator-class="el-icon-arrow-right" class="breadcrumb">
    <el-breadcrumb-item to="/home">首頁</el-breadcrumb-item>
    <el-breadcrumb-item to="/about">關於我們</el-breadcrumb-item>
    <el-breadcrumb-item to="/contact">聯繫我們</el-breadcrumb-item>
  </el-breadcrumb>
</template>
  
<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Breadcrumbs',
});
</script>
  
<style scoped>
.breadcrumb {
  margin-top: 20px;
  font-size: 20px;
}
</style>