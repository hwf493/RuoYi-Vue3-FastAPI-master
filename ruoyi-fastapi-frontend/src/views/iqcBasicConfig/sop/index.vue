<template>
  <div class="app-container">
    <el-card shadow="hover" class="iqc-card">
      <template #header>
        <div class="card-header">
          <svg-icon icon-class="clipboard" class="header-icon" />
          <span class="header-title">SOP 配置</span>
        </div>
      </template>

      <el-alert
        title="静态占位页面"
        type="info"
        description="该页面用于维护 IQC 作业指导书 (SOP)，关联标准书与具体作业步骤。"
        :closable="false"
        show-icon
      />

      <el-descriptions
        title="SOP 信息"
        :column="2"
        border
        style="margin-top: 20px"
      >
        <el-descriptions-item label="SOP 编号">待维护</el-descriptions-item>
        <el-descriptions-item label="SOP 名称">待维护</el-descriptions-item>
        <el-descriptions-item label="关联标准书">待维护</el-descriptions-item>
        <el-descriptions-item label="作业步骤数">待维护</el-descriptions-item>
        <el-descriptions-item label="责任人">待维护</el-descriptions-item>
        <el-descriptions-item label="状态">待发布</el-descriptions-item>
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