<template>
  <Index v-bind="$props" type="pie" />
</template>

<script>
import Index from './index'
import 'echarts/lib/chart/pie'
export default {
  components: {
    Index
  },

  props: {
    ...Index.props
  }
}
</script>

<style>
</style>
