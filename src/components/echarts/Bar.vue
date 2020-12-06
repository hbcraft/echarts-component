<template>
  <Index v-bind="$props" type="bar" />
</template>

<script>
import Index from './index'
import 'echarts/lib/chart/bar'
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
