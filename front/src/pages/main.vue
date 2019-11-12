<template>
  <div class="flex auto column" style="height:100%;">
    <div class="title">이채 주방가구</div>
    <div style="overflow-y:auto; margin-bottom:30px;">
      <estimate name="상부장" price="1.2" type="upper_cb"></estimate>
      <estimate name="하부장" price="1.2" type="lower_cb"></estimate>
    </div>

  </div>
</template>
<script>

import Estimate from '@/components/estimate'

export default {
  name: 'mian',
  components:{
    Estimate,
  },
  data () {
    return {
  
    }
  },
  methods:{
  },
  async mounted(){
  
  },
}
</script>

<style scoped lang="scss">
</style>
