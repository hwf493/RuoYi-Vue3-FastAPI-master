<template>
  <div class="app-container">
    <el-card shadow="hover" class="iqc-card">
      <template #header>
        <div class="card-header">
          <svg-icon icon-class="tree" class="header-icon" />
          <span class="header-title">规则配置</span>
        </div>
      </template>

      <el-alert
        title="静态占位页面"
        type="success"
        description="该页面用于配置 IQC 抽检规则、跳转规则、放行规则等业务规则。"
        :closable="false"
        show-icon
      />

      <el-descriptions
        title="规则信息"
        :column="2"
        border
        style="margin-top: 20px"
      >
        <el-descriptions-item label="规则编号">R001</el-descriptions-item>
        <el-descriptions-item label="规则名称">正常抽检</el-descriptions-item>
        <el-descriptions-item label="规则类型">抽样</el-descriptions-item>
        <el-descriptions-item label="检验水平">II</el-descriptions-item>
        <el-descriptions-item label="AQL">1.0</el-descriptions-item>
        <el-descriptions-item label="状态">启用</el-descriptions-item>
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