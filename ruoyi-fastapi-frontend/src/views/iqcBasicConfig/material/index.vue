<template>
  <div class="app-container">
    <el-card shadow="hover" class="iqc-card">
      <template #header>
        <div class="card-header">
          <svg-icon icon-class="documentation" class="header-icon" />
          <span class="header-title">物料主信息</span>
        </div>
      </template>

      <el-alert
        title="静态占位页面"
        type="info"
        description="该页面用于维护 IQC 检验所需的物料主数据。可在此扩展物料编号、物料名称、规格型号、检验类型等字段。"
        :closable="false"
        show-icon
      />

      <el-descriptions
        title="基础信息"
        :column="2"
        border
        style="margin-top: 20px"
      >
        <el-descriptions-item label="物料编号">待维护</el-descriptions-item>
        <el-descriptions-item label="物料名称">待维护</el-descriptions-item>
        <el-descriptions-item label="规格型号">待维护</el-descriptions-item>
        <el-descriptions-item label="检验类型">待维护</el-descriptions-item>
        <el-descriptions-item label="默认检验水平">待维护</el-descriptions-item>
        <el-descriptions-item label="AQL 值">待维护</el-descriptions-item>
      </el-descriptions>
    </el-card>
  </div>
</template>

<script setup>
</script>

<style lang="scss" scoped>
.iqc-card {
  min-height: calc(100vh - 110px);
}
.card-header {
  display: flex;
  align-items: center;
  font-size: 16px;
  font-weight: 600;
}
.header-icon {
  margin-right: 8px;
  width: 18px;
  height: 18px;
}
.header-title {
  color: #303133;
}
</style>