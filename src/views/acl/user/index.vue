<template>
  <div>
    <!-- 搜素区域 -->
    <div class="search-view">
      <el-input
        placeholder="请输入用户名"
        style="width: 150px; margin-right: 10px"
      />
      <el-button type="primary" icon="el-icon-search">查询</el-button>
      <el-button>清空</el-button>
    </div>
    <!-- 操作区域 -->
    <div class="opera-view">
      <el-button type="primary">添加</el-button>
      <el-button type="danger">批量删除</el-button>
    </div>
    <!-- 表格区域 -->
    <el-table
      v-loading="isLoading"
      :data="trademarkList"
      class="mg-20"
      style="width: 100%"
      border
      stripe
      :header-cell-style="{ color: '#409eff' }"
    >
      <!-- 表格项 -->
      <el-table-column label="序号" type="index" width="100px" align="center" />
      <el-table-column type="selection" />
      <el-table-column label="用户名" prop="tmName" />
      <el-table-column label="用户昵称" prop="tmName" />
      <el-table-column label="权限列表" prop="tmName" />
      <el-table-column label="创建时间" prop="tmName" />
      <el-table-column label="更新时间" prop="tmName" />
      <el-table-column label="操作">
        <template v-slot="{ row }">
          <el-button
            style="margin-right: 10px"
            type="warning"
            size="mini"
            icon="el-icon-edit"
            @click="updateTrademark(row)"
            >修改</el-button
          >
          <el-popconfirm
            title="你确定要删除吗?"
            icon="el-icon-delete"
            icon-color="#409eff"
            @onConfirm="deleteTrademark(row.id)"
          >
            <el-button
              slot="reference"
              type="danger"
              size="mini"
              icon="el-icon-delete"
              >删除</el-button
            >
          </el-popconfirm>
        </template>
      </el-table-column>
    </el-table>
    <!-- 分页器 -->
    <el-pagination
      style="text-align: center"
      background
      layout="prev, pager, next, jumper, ->, total, sizes"
      :total="total"
      :page-sizes="[5, 10, 20]"
      :page-size="limit"
      :current-page="page"
      @current-change="pageChange"
      @size-change="sizeChange"
    />
  </div>
</template>

<script>
export default {};
</script>

<style lang="sass" scoped>
.search-input
  width: 200px
  margin-right: 10px

.opera-view
  margin: 20px 0
</style>
