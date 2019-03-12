<template>
  <div>
    <div v-for="(item, index) in bardatas" :key="index">
        <div :id="item.id" style="width:80%;height:600px;" class="pull-left"></div>
    </div>
  <!--  <div id="test" style="width:400px;height:300px;"></div> -->
  </div>
</template>

<script>

export default{
  data () {
    return {
      busname: ''
    }
  },
  props: {
    bardatas: {
      type: Array,
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
      for (const i in this.bardatas) {
        if (Object.prototype.hasOwnProperty.call(this.bardatas, i)) {
          const myChart = this.$echarts.init(document.getElementById(this.bardatas[i].id))
          const option = {
          // myChart.setOption({
            color: ['#3398DB'],
            tooltip: {
              trigger: 'axis',
              axisPointer: { // 坐标轴指示器，坐标轴触发有效
                type: 'shadow' // 默认为直线，可选为：'line' | 'shadow'
              }
            },
            grid: {
              left: '3%',
              right: '4%',
              bottom: '3%',
              containLabel: true
            },
            xAxis: [
              {
                type: 'value'
              }
            ],
            yAxis: [
              {
                type: 'category',
                data: this.bardatas[i].yAxis,
                axisTick: {
                  alignWithLabel: true
                }
              }
            ],
            series: [
              {
                name: '直接访问',
                type: 'bar',
                barWidth: '60%',
                data: this.bardatas[i].series
              }
            ]
          }
          myChart.setOption(option)
          myChart.on('click', (res) => {
            this.$emit('busname', {
              busname: res.name
            })
          })
        }
      }
    }
  },
  watch: {
    bardatas: {
      handler (val) {
        this.bardatas = val
        setTimeout(() => {
          this.charts()
        }, 1000)
      }
    }
  }
}
</script>
