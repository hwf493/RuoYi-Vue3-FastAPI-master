<template>
  <div class="app-container">
    <el-card shadow="hover" class="iqc-card">
      <template #header>
        <div class="card-header">
          <svg-icon icon-class="list" class="header-icon" />
          <span class="header-title">检验任务</span>
        </div>
      </template>

      <el-alert
        title="静态占位页面"
        type="info"
        description="该页面用于维护质检管理下的检验任务，包括任务分配、优先级、执行状态等。"
        :closable="false"
        show-icon
      />

      <el-descriptions
        title="检验任务信息"
        :column="2"
        border
        style="margin-top: 20px"
      >
        <el-descriptions-item label="任务编号">待维护</el-descriptions-item>
        <el-descriptions-item label="任务名称">待维护</el-descriptions-item>
        <el-descriptions-item label="关联物料">待维护</el-descriptions-item>
        <el-descriptions-item label="检验类型">待维护</el-descriptions-item>
        <el-descriptions-item label="优先级">待维护</el-descriptions-item>
        <el-descriptions-item label="执行状态">待处理</el-descriptions-item>
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
