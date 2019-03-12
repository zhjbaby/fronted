<template>
  <div>
    <el-menu default-active="1-4-1" class="el-menu-vertical-demo" :collapse="isCollapse">
      <el-menu-item index="1">
        <i class="el-icon-menu"></i>
        <span slot="title">导航1</span>
      </el-menu-item>
      <el-menu-item index="2">
        <i class="el-icon-document"></i>
        <span slot="title">导航2</span>
      </el-menu-item>
      <el-menu-item index="3">
        <i class="el-icon-news"></i>
        <span slot="title">导航3</span>
      </el-menu-item>
      <el-menu-item index="4">
        <i class="el-icon-message"></i>
        <span slot="title">导航4</span>
      </el-menu-item>
      <el-menu-item index="5">
        <i class="el-icon-printer"></i>
        <span slot="title">导航5</span>
      </el-menu-item>
      <el-menu-item index="6">
        <i class="el-icon-tickets"></i>
        <span slot="title">导航6</span>
      </el-menu-item>
      <el-menu-item index="7">
        <i class="el-icon-view"></i>
        <span slot="title">导航7</span>
      </el-menu-item>
      <el-menu-item index="8">
        <i class="el-icon-edit-outline"></i>
        <span slot="title">导航8</span>
      </el-menu-item>
    </el-menu>
  </div>
</template>

<script>

import Bus from '../../assets/bus'

export default {
  name: 'side',
  data () {
    return {
      isCollapse: false
    }
  },
  methods: {
  },
  created () {
    Bus.$on('is', (status) => {
      this.isCollapse = status
    })
  }
}
</script>

<style>
.el-menu-vertical-demo:not(.el-menu--collapse) {
  min-width: 200px;
  min-height: 400px;
}
</style>
