<template>
  <div class="app-container">
    <el-card shadow="hover" class="iqc-card">
      <template #header>
        <div class="card-header">
          <svg-icon icon-class="bug" class="header-icon" />
          <span class="header-title">不良代码（外观）</span>
        </div>
      </template>

      <el-alert
        title="静态占位页面"
        type="warning"
        description="该页面用于维护外观不良代码库，IQC 检验时可直接引用。"
        :closable="false"
        show-icon
      />

      <el-descriptions
        title="不良代码示例"
        :column="2"
        border
        style="margin-top: 20px"
      >
        <el-descriptions-item label="代码编号">D001</el-descriptions-item>
        <el-descriptions-item label="不良名称">划痕</el-descriptions-item>
        <el-descriptions-item label="不良类别">外观</el-descriptions-item>
        <el-descriptions-item label="严重等级">轻微</el-descriptions-item>
        <el-descriptions-item label="判定标准">待维护</el-descriptions-item>
        <el-descriptions-item label="备注">-</el-descriptions-item>
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
  color: #e6a23c;
}
.header-title {
  color: #303133;
}
</style>