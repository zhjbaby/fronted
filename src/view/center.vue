<template>
  <div>
    <div>
    <el-radio-group v-model="isCollapse" @change="open" size="small">
      <el-radio-button :label="false">展开</el-radio-button>
      <el-radio-button :label="true">收起</el-radio-button>
    </el-radio-group>
    </div>
    <div>
    <iframe :src="uri" style="width:100%;" id="if" ref="iframe" frameborder="no">
    </iframe>
    </div>
  </div>
</template>

<script>

import Bus from '../assets/bus'

export default {
  name: 'center',
  data () {
    return {
      isCollapse: false,
      uri: ''
    }
  },
  methods: {
    open () {
      Bus.$emit('is', this.isCollapse)
    },
    changesize () {
      const oIframe = document.getElementById('if')
      const deviceWidth = document.documentElement.clientWidth
      const deviceHeight = document.documentElement.clientHeight
      oIframe.style.width = (Number(deviceWidth) - 220) + 'px'
      oIframe.style.height = (Number(deviceHeight) - 120) + 'px'
    }
  },
  created () {
  },
  mounted () {
  }
}
</script>

<style>
</style>
