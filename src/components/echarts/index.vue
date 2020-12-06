<template>
  <div :id="elId" :style="chartStyle"></div>
</template>

<script>
import UUID from 'uuid/v1'
import echarts from 'echarts/lib/echarts'

import 'echarts/lib/component/title'
import 'echarts/lib/component/legend'
import 'echarts/lib/component/tooltip'

export default {
  data () {
    return {
      elId: '',
      myChart: ''
    }
  },

  computed: {
    chartOption () {
      let series = []
      const legendData = []
      if (this.datas[0] instanceof Object) {
        if (this.type === 'pie') {
          series.push({
            type: this.type,
            data: []
          })
          this.datas[0].data.map((v, i) => {
            series[0].data.push({
              name: this.names[i],
              value: v
            })
          })
        } else {
          series = this.datas.map((v) => {
            v.type = this.type
            v.label = v.name
            legendData.push(v.name)
            return v
          })
        }
      } else {
        if (this.type === 'pie') {
          series.push({
            type: this.type,
            data: []
          })
          this.datas.map((v, i) => {
            series[0].data.push({
              name: this.names[i],
              value: v
            })
          })
        } else {
          series.push({
            type: this.type,
            data: this.datas
          })
        }
      }
      return {
        title: {
          text: this.title
        },
        legend: {
          data: legendData
        },
        tooltip: {},
        xAxis: {
          data: this.names
        },
        yAxis: {},
        series: series
      }
    },
    chartStyle () {
      return {
        width: this.width,
        height: this.height
      }
    }
  },

  props: {
    datas: {
      type: Array,
      required: true
    },
    names: {
      type: Array,
      required: true
    },
    title: {
      type: String
    },
    width: {
      type: String,
      default: '100%'
    },
    height: {
      type: String,
      default: '100%'
    },
    type: {
      type: String
    }
  },

  created () {
    this.elId = UUID()
  },

  watch: {
    data: {
      handler: function (value, oldValue) {
        this.myChart.setOption(this.chartOption)
      },
      deep: true
    }
  },

  mounted () {
    this.myChart = echarts.init(document.getElementById(this.elId))
    this.myChart.setOption(this.chartOption)
    console.log(this)
  }
}
</script>

<style>
</style>
