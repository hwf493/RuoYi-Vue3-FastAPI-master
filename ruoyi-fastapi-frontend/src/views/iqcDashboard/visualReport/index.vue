<template>
  <div class="app-container">
    <el-card shadow="hover" class="iqc-card">
      <template #header>
        <div class="card-header">
          <svg-icon icon-class="chart" class="header-icon" />
          <span class="header-title">IQC可视化报表</span>
        </div>
      </template>

      <el-alert
        title="静态占位页面"
        type="success"
        description="该页面用于展示 IQC 来料检验的可视化报表，包括合格率趋势、不良分布、检验批次统计等图表。"
        :closable="false"
        show-icon
      />

      <el-descriptions
        title="看板指标示例"
        :column="2"
        border
        style="margin-top: 20px"
      >
        <el-descriptions-item label="今日来料批次">待维护</el-descriptions-item>
        <el-descriptions-item label="抽检合格率">待维护</el-descriptions-item>
        <el-descriptions-item label="不良批次数">待维护</el-descriptions-item>
        <el-descriptions-item label="平均检验时长">待维护</el-descriptions-item>
        <el-descriptions-item label="TOP3 不良类别">待维护</el-descriptions-item>
        <el-descriptions-item label="数据更新时间">待维护</el-descriptions-item>
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
