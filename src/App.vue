<template>
  <div id="app" style="width: 800px; height: 600px">
    <EchartsPie :datas="chartData" :names="chartNames" :title="chartTitle" />
  </div>
</template>

<script>
// import EchartsBar from './components/echarts/Bar'
import EchartsPie from './components/echarts/Pie'

export default {
  name: 'App',
  data () {
    return {
      chartTitle: '233',
      chartData: [{
        name: '233',
        data: [5, 20, 36, 10, 10, 20]
      }, {
        name: '666',
        data: [10, 20, 36, 10, 10, 20]
      }, {
        name: '555',
        data: [15, 20, 36, 10, 10, 20]
      }, {
        name: '888',
        data: [20, 20, 36, 10, 10, 20]
      }],
      chartNames: ['衬衫', '羊毛衫', '雪纺衫', '裤子', '高跟鞋', '袜子']
    }
  },
  components: {
    // EchartsBar,
    EchartsPie
  },
  mounted () {
  },
  methods: {
  }
}
</script>

<style lang="scss">
</style>
