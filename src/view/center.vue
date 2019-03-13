<template>
  <div>
    <div>
    <el-radio-group v-model="isCollapse" @change="open" size="small">
      <el-radio-button :label="false">展开</el-radio-button>
      <el-radio-button :label="true">收起</el-radio-button>
    </el-radio-group>
    </div>
    <div>
      <div>
        <Chart :bardatas="datas"></Chart>
        <Lines :linedatas="linedata"></Lines>
      </div>
      <div>
        <span>翻页</span>
        <Page :count="num"></Page>
      </div>
    </div>
  </div>
</template>

<script>

import Bus from '../assets/bus'
import Chart from '../components/common/chart_bar'
import Lines from '../components/common/chart_line'
import Page from '../components/common/page'

export default {
  name: 'center',
  components: {
    Chart,
    Lines,
    Page
  },
  data () {
    return {
      isCollapse: false,
      uri: '',
      search: '',
      num: 100,
      datas: [
        {
          id: 'a',
          title: '饼图',
          series: [
            {
              value: 45,
              name: 'test1'
            },
            {
              value: 55,
              name: 'test2'
            }
          ]
        }
      ],
      linedata: {
        title: '折线图',
        legend: ['邮件营销', '联盟广告', '视频广告', '直接访问', '搜索引擎'],
        xAxis: ['周一', '周二', '周三', '周四', '周五', '周六', '周日'],
        series: [
          {
            name: '邮件营销',
            type: 'line',
            stack: '总量',
            data: [120, 132, 101, 134, 90, 230, 210]
          },
          {
            name: '联盟广告',
            type: 'line',
            stack: '总量',
            data: [220, 182, 191, 234, 290, 330, 310]
          },
          {
            name: '视频广告',
            type: 'line',
            stack: '总量',
            data: [150, 232, 201, 154, 190, 330, 410]
          },
          {
            name: '直接访问',
            type: 'line',
            stack: '总量',
            data: [320, 332, 301, 334, 390, 330, 320]
          },
          {
            name: '搜索引擎',
            type: 'line',
            stack: '总量',
            data: [820, 932, 901, 934, 1290, 1330, 1320]
          }
        ]
      }
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
