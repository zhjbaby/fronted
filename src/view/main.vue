<template>
  <div>
    <div style="">
      <el-header>平台建设</el-header>
    </div>
    <div>
      <div style="float:left;" :class="{ big: !isCollapse, small: isCollapse }">
        <t-side></t-side>
      </div>
      <div style="float:left;" :class="{ rbig: isCollapse, rsmall: !isCollapse }">
        <t-body></t-body>
      </div>
    </div>
  </div>
</template>

<script>

import Bus from '../assets/bus'
import Side from '../components/common/sidebar'
import Body from './center'

export default {
  name: 'Main',
  data () {
    return {
      isCollapse: false
    }
  },
  components: {
    't-side': Side,
    't-body': Body
  },
  created () {
    Bus.$on('is', (status) => {
      this.isCollapse = status
    })
  }
}
</script>

<style>
.big {
  width: 16%;
}
.small {
  width: 5.3%;
}
.rbig {
  width: 94%;
}
.rsmall {
  width: 83.5%;
}
</style>
