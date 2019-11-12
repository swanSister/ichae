<template>
  <div class="flex none sub-title justify-content-center align-items-center" style="padding:2vw;">
    <div @click="backHandler" class="flex none icon-left-small" style="width:10vw; color:#595959;"></div>
    <div class="flex auto justify-content-center">
      <div style="margin-left:-10vw;">{{title}}</div>
    </div>
  </div>
</template>

<script>
export default {
  props:{
    title:String,
  },
  data () {
    return {
    
    }
  },
  methods:{
    backHandler(){
      console.log("history length : " + window.history.length)
      if(window.history.length>2){
        this.$router.go(-1)
      }else{
         this.$router.push('main')
      }
    }

  },
  mounted(){
  
  }
}
</script>
<style scoped>

</style>