<template>
  <div class="app-container">
    <el-card shadow="hover" class="data-analysis-card">
      <template #header>
        <div class="card-header">
          <svg-icon icon-class="analysis" class="header-icon" />
          <span class="header-title">数据分析看板</span>
          <el-tag size="small" type="info" style="margin-left: 12px;">实时</el-tag>
          <div class="header-actions">
            <el-button size="small" type="primary" plain @click="handleRefresh">
              <svg-icon icon-class="refresh" /> 刷新
            </el-button>
            <el-button size="small" plain @click="handleExport">
              <svg-icon icon-class="export" /> 导出
            </el-button>
          </div>
        </div>
      </template>

      <!-- 概览指标卡片 -->
      <el-row :gutter="16" class="stat-cards">
        <el-col :xs="12" :sm="6" v-for="stat in statistics" :key="stat.label">
          <div class="stat-item" :class="stat.color">
            <div class="stat-icon">
              <svg-icon :icon-class="stat.icon" />
            </div>
            <div class="stat-content">
              <div class="stat-value">{{ stat.value }}</div>
              <div class="stat-label">{{ stat.label }}</div>
              <div class="stat-trend" v-if="stat.trend">
                <span :class="stat.trend > 0 ? 'trend-up' : 'trend-down'">
                  {{ stat.trend > 0 ? '↑' : '↓' }} {{ Math.abs(stat.trend) }}%
                </span>
                <span class="trend-period">较昨日</span>
              </div>
            </div>
          </div>
        </el-col>
      </el-row>

      <!-- 图表区域 -->
      <el-row :gutter="16" style="margin-top: 16px;">
        <el-col :xs="24" :lg="14">
          <el-card shadow="never" class="chart-card">
            <template #header>
              <span class="chart-title">趋势分析</span>
              <el-radio-group v-model="trendPeriod" size="small" style="float: right;">
                <el-radio-button label="week">周</el-radio-button>
                <el-radio-button label="month">月</el-radio-button>
                <el-radio-button label="quarter">季</el-radio-button>
              </el-radio-group>
            </template>
            <div class="chart-placeholder">
              <svg-icon icon-class="chart-line" class="placeholder-icon" />
              <span>趋势图占位 (ECharts 折线图)</span>
            </div>
          </el-card>
        </el-col>
        <el-col :xs="24" :lg="10">
          <el-card shadow="never" class="chart-card">
            <template #header>
              <span class="chart-title">数据分布</span>
            </template>
            <div class="chart-placeholder">
              <svg-icon icon-class="chart-pie" class="placeholder-icon" />
              <span>分布图占位 (ECharts 饼图)</span>
            </div>
          </el-card>
        </el-col>
      </el-row>

      <!-- 数据表格 -->
      <el-row :gutter="16" style="margin-top: 16px;">
        <el-col :span="24">
          <el-card shadow="never" class="table-card">
            <template #header>
              <span class="chart-title">明细数据</span>
              <div style="float: right;">
                <el-input
                  v-model="searchKeyword"
                  placeholder="搜索..."
                  size="small"
                  prefix-icon="Search"
                  style="width: 200px; margin-right: 8px;"
                />
                <el-button size="small" type="primary" plain>筛选</el-button>
              </div>
            </template>
            <el-table :data="tableData" stripe border style="width: 100%">
              <el-table-column prop="id" label="ID" width="60" align="center" />
              <el-table-column prop="category" label="分类" min-width="120" />
              <el-table-column prop="indicator" label="指标名称" min-width="150" />
              <el-table-column prop="value" label="数值" width="120" align="right" />
              <el-table-column prop="change" label="变化" width="100" align="center">
                <template #default="{ row }">
                  <el-tag :type="row.change > 0 ? 'success' : 'danger'" size="small">
                    {{ row.change > 0 ? '+' : '' }}{{ row.change }}%
                  </el-tag>
                </template>
              </el-table-column>
              <el-table-column prop="updateTime" label="更新时间" width="170" align="center" />
              <el-table-column label="操作" width="120" align="center" fixed="right">
                <template #default>
                  <el-button size="small" type="text" @click="handleDetail">详情</el-button>
                </template>
              </el-table-column>
            </el-table>
            <div class="table-pagination">
              <el-pagination
                background
                layout="total, sizes, prev, pager, next"
                :total="100"
                :page-sizes="[10, 20, 50]"
                v-model:page-size="pageSize"
                v-model:current-page="currentPage"
              />
            </div>
          </el-card>
        </el-col>
      </el-row>
    </el-card>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'

// 概览统计
const statistics = reactive([
  {
    label: '总数据量',
    value: '128.5K',
    icon: 'database',
    color: 'primary',
    trend: 12.5
  },
  {
    label: '活跃用户',
    value: '3,842',
    icon: 'user',
    color: 'success',
    trend: 8.3
  },
  {
    label: '转化率',
    value: '24.8%',
    icon: 'rate',
    color: 'warning',
    trend: -2.1
  },
  {
    label: '平均响应',
    value: '1.2s',
    icon: 'time',
    color: 'info',
    trend: -5.7
  }
])

// 趋势周期
const trendPeriod = ref('week')

// 表格数据
const tableData = ref([
  { id: 1, category: '用户行为', indicator: '日活跃用户数', value: 3842, change: 8.3, updateTime: '2026-08-27 14:32' },
  { id: 2, category: '业务指标', indicator: '订单完成率', value: 92.6, change: 3.1, updateTime: '2026-08-27 14:30' },
  { id: 3, category: '系统性能', indicator: 'API 平均耗时', value: 1.2, change: -5.7, updateTime: '2026-08-27 14:28' },
  { id: 4, category: '用户行为', indicator: '新增注册用户', value: 156, change: 15.2, updateTime: '2026-08-27 14:25' },
  { id: 5, category: '业务指标', indicator: '客单价', value: 328.5, change: 2.4, updateTime: '2026-08-27 14:20' }
])

// 分页
const currentPage = ref(1)
const pageSize = ref(10)
const searchKeyword = ref('')

// 方法
const handleRefresh = () => {
  console.log('刷新数据')
}
const handleExport = () => {
  console.log('导出数据')
}
const handleDetail = () => {
  console.log('查看详情')
}
</script>

<style lang="scss" scoped>
.data-analysis-card {
  min-height: calc(100vh - 110px);
}

.card-header {
  display: flex;
  align-items: center;
  font-size: 16px;
  font-weight: 600;
  width: 100%;

  .header-icon {
    margin-right: 8px;
    width: 18px;
    height: 18px;
  }

  .header-actions {
    margin-left: auto;
    display: flex;
    gap: 8px;
  }
}

// 统计卡片
.stat-cards {
  margin: 0 -8px;

  .stat-item {
    background: #fafafa;
    border-radius: 8px;
    padding: 16px 20px;
    display: flex;
    align-items: center;
    transition: all 0.3s;
    border-left: 4px solid #909399;

    &:hover {
      transform: translateY(-2px);
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
    }

    .stat-icon {
      width: 44px;
      height: 44px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      background: rgba(64, 158, 255, 0.1);
      margin-right: 14px;
      flex-shrink: 0;

      .svg-icon {
        width: 22px;
        height: 22px;
      }
    }

    .stat-content {
      flex: 1;
      min-width: 0;

      .stat-value {
        font-size: 24px;
        font-weight: 700;
        color: #303133;
        line-height: 1.2;
      }

      .stat-label {
        font-size: 13px;
        color: #909399;
        margin-top: 2px;
      }

      .stat-trend {
        margin-top: 4px;
        font-size: 12px;

        .trend-up {
          color: #67c23a;
        }
        .trend-down {
          color: #f56c6c;
        }
        .trend-period {
          color: #c0c4cc;
          margin-left: 4px;
        }
      }
    }

    &.primary {
      border-left-color: #409eff;
      .stat-icon {
        background: rgba(64, 158, 255, 0.1);
        color: #409eff;
      }
    }
    &.success {
      border-left-color: #67c23a;
      .stat-icon {
        background: rgba(103, 194, 58, 0.1);
        color: #67c23a;
      }
    }
    &.warning {
      border-left-color: #e6a23c;
      .stat-icon {
        background: rgba(230, 162, 60, 0.1);
        color: #e6a23c;
      }
    }
    &.info {
      border-left-color: #909399;
      .stat-icon {
        background: rgba(144, 147, 153, 0.1);
        color: #909399;
      }
    }
  }
}

// 图表卡片
.chart-card {
  height: 100%;

  :deep(.el-card__header) {
    border-bottom: 1px solid #ebeef5;
    padding: 12px 20px;

    .chart-title {
      font-weight: 600;
      font-size: 14px;
      color: #303133;
    }
  }

  :deep(.el-card__body) {
    padding: 20px;
  }
}

.chart-placeholder {
  height: 220px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background: #fafbfc;
  border-radius: 6px;
  border: 1px dashed #dcdfe6;
  color: #909399;
  font-size: 13px;

  .placeholder-icon {
    width: 48px;
    height: 48px;
    color: #c0c4cc;
    margin-bottom: 8px;
  }
}

// 表格卡片
.table-card {
  :deep(.el-card__header) {
    border-bottom: 1px solid #ebeef5;
    padding: 12px 20px;

    .chart-title {
      font-weight: 600;
      font-size: 14px;
      color: #303133;
    }
  }

  :deep(.el-card__body) {
    padding: 16px 20px;
  }
}

.table-pagination {
  display: flex;
  justify-content: flex-end;
  margin-top: 16px;
}
</style>