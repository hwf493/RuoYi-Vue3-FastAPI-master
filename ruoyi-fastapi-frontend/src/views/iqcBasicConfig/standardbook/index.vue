<template>
  <div class="app-container">
    <el-card shadow="hover" class="iqc-card">
      <template #header>
        <div class="card-header">
          <svg-icon icon-class="form" class="header-icon" />
          <span class="header-title">标准书配置</span>
        </div>
      </template>

      <el-alert
        title="静态占位页面"
        type="info"
        description="该页面用于配置 IQC 检验标准书，包括检验项目、判定标准、抽样方案等。"
        :closable="false"
        show-icon
      />

      <el-descriptions
        title="标准书信息"
        :column="2"
        border
        style="margin-top: 20px"
      >
        <el-descriptions-item label="标准书编号">待维护</el-descriptions-item>
        <el-descriptions-item label="标准书名称">待维护</el-descriptions-item>
        <el-descriptions-item label="适用物料类别">待维护</el-descriptions-item>
        <el-descriptions-item label="版本号">V1.0</el-descriptions-item>
        <el-descriptions-item label="生效日期">待维护</el-descriptions-item>
        <el-descriptions-item label="状态">草稿</el-descriptions-item>
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