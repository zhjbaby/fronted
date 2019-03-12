<template>
  <div>
    <div id="myChart" style="width:950px;height:600px;" class="pull-left"></div>
  </div>
</template>

<script>
let my = Object

export default {
  data () {
    return {
      my: Object
    }
  },
  props: {
    linedatas: {
      type: Object,
      required: true
    }
  },
  created () {
  },
  mounted () {
    this.charts()
  },
  methods: {
    charts () {
      for (const value of this.linedatas.series) {
        value.type = 'line'
      }
      my = this.$echarts.init(document.getElementById('myChart'))
      const option = {
        title: {
          text: this.linedatas.title
        },
        tooltip: {
          trigger: 'axis'
        },
        legend: {
          // show: false,
          // selectedMode: false,
          selected: {},
          data: this.linedatas.legend,
          left: '20%'
        },
        grid: {
          left: '3%',
          right: '4%',
          bottom: '3%',
          containLabel: true
        },
        toolbox: {
          feature: {
            saveAsImage: {}
          }
        },
        xAxis: {
          type: 'category',
          boundaryGap: false,
          data: this.linedatas.xAxis
        },
        yAxis: {
          type: 'value'
        },
        series: this.linedatas.series
      }
      my.setOption(option)
      my.on('legendselectchanged', (res) => {
        const lengendArr = option.legend.data
        for (let i = 0; i < lengendArr.length; i += 1) {
          option.legend.selected[lengendArr[i]] = false // 所有的都不选中
        }
        option.legend.selected[res.name] = true // 选中点击的那个元素
        my.setOption(option, true) // 重新绘制
      })
    }
  },
  watch: {
    linedatas: {
      handler (val) {
        this.linedatas = val
        setTimeout(() => {
          this.charts()
        }, 1000)
      }
    }
  }
}
</script>
