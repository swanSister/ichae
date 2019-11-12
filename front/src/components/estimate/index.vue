<template>
  <div class="flex none align-items-start estimate">
    <div class="flex icon none column align-items-center">
      <div class="flex none name justify-content-start">{{name}}</div>
      <img :src="require(`@/assets/icon/${type}.png`)"/>
    </div>
    <div class="flex box column">
      <div class="flex" style="width:100%;">
        <div class="flex auto justify-content-start align-items-center">
          <div class="red-button flex none align-items-center select-popup">자재</div>
          <input style="width:20%;" class="input" placeholder="가로" @keydown="onKeydown" />
          <div class="flex none align-items-center justify-content-center" style="margin:0 0.5vw 0 1.5vw; font-size:2vw; ">X</div>
          <input style="width:20%; margin-left:1vw;" class="input" placeholder="세로" @keydown="onKeydown"/>
        </div>

        <div class="flex none justify-content-end" style="min-width:30%;">
          <div class="flex auto price align-items-center justify-content-end">397.2<span class="prefix">만원</span></div>
        </div>
      </div>
      <div v-if="type==`upper_cb`" style="padding-left:2vw; margin-top:4vw;" class="flex align-items-center">
        <div class="flex auto justify-content-start align-items-center">
          <label class="checkbox-container">후드
            <input type="checkbox" v-model="isHoodSelect">
            <span class="checkmark"></span>
          </label>
          <div v-if="isHoodSelect" class="red-button flex none align-items-center select-popup">선택</div>
        </div>
        <div class="flex none justify-content-end" style="min-width:30%;">
          <div class="flex auto price align-items-center justify-content-end">0<span class="prefix">만원</span></div>
        </div>
      </div>

      <div v-if="type==`lower_cb`" style="padding-left:2vw; margin-top:4vw;" class="flex align-items-center">
        <div class="flex auto justify-content-start align-items-center">
          <label class="checkbox-container">씽크볼
            <input type="checkbox" v-model="isSinkballSelect">
            <span class="checkmark"></span>
          </label>
          <div v-if="isSinkballSelect" class="red-button flex none align-items-center select-popup">선택</div>
        </div>
        <div class="flex none justify-content-end" style="min-width:30%;">
          <div class="flex auto price align-items-center justify-content-end">0<span class="prefix">만원</span></div>
        </div>
      </div>
    
    </div>
  </div>
</template>

<script>
export default {
  props:{
    name:String,
    type:String,
  },
  data () {
    return {
      selectedDate:null,
      isCalendarShow:false,
      isHoodSelect:false,
      isSinkballSelect:false,
    }
  },
  computed: {

  },
  methods:{
    onKeydown(e){

    },
  },
  mounted(){

   
  }
}
</script>
<style scoped>
.estimate{
  flex-direction: column;
  font-size:6vw;
  padding: 5vw 2vw;
  border-bottom: 0.6vw dashed rgba(33, 38, 46, 0.3);
}
.estimate .icon{
  font-size:4vw;
  padding:2vw;
  border-radius: 0.6vw;
  background:rgba(197, 197, 197, 0.5);
  width:100%;
  height:100%;
}
.estimate .icon img{
  margin-top: 2vw;
  width:100%;
  height:auto;
  vertical-align: middle;
}
.estimate .box{
  width:100%;
  margin-top:4vw;
}
.estimate .price{
  padding:0 1vw;
  margin-left:4vw;
  font-size:6vw;
  color:rgba(252, 107, 24,1);
  border-bottom: 1px dashed black;
}
.estimate .price .prefix{
  font-size:3vw;
  margin-left:1vw;
  color:#2D3642;
  opacity:.7;
}
@media ( min-width: 768px ) {
  .estimate{
    font-size:3vw;
    flex-direction: row;
    padding: 2.5vw 1vw;
    border-bottom: 0.3vw dashed rgba(33, 38, 46, 0.3);
  }
  .estimate .icon{
    font-size: 2vw;
    width:30%;
  }
  .estimate .icon img{
    margin-top:1vw;
  }
  .estimate .box{
    margin-top:0;
    width:70%;
  }
  .estimate .price{
    padding:0 0.5vw;
    margin-left:2vw;
    font-size:3vw;
  }
  .estimate .price .prefix{
    font-size:1.5vw;
    margin-left:0.5vw;
  }
}
</style>