<template>
  <div class="flex column none align-items-center">
    <div class="flex auto date-picker " @click="!calendarDisable ? isCalendarShow = !isCalendarShow : null">
      <div class="flex none side-content align-items-center"><div class="icon-calendar title-icon"/></div>
      <div class="flex auto align-items-center justify-content-center"> {{$moment(startTime).format('YYYY.MM.DD')}} ~ {{endTime ? endTime : ''}}</div>
      <div class="flex none side-content align-items-center"></div>
    </div>
    <div v-if="isCalendarShow" class="popup-bg" @click="isCalendarShow=false" style="background:transparent;"></div>
    <div v-if="isCalendarShow" class="flex calendar" style="margin-top:1vw; flex-wrap: wrap; z-index:5;">
      <div class="flex auto" style="width:100%; padding:2vw 0; ">
        <div @click="onPrevClick" class="flex none side-content align-items-center"><div class="icon-angle-left title-icon"/></div>
        <div class="flex auto align-items-center justify-content-center">{{ $moment(selectedDate).format('YYYY년 MM월') }} </div>
        <div @click="onNextClick" class="flex none side-content align-items-center"><div class=" icon-angle-right title-icon"/></div>
      </div>
      <div class="flex auto align-items-center justify-content-center calendar-cell" style="margin: 2vw 0; font-size:3vw;"
      v-for="(item, index) of ['월', '화', '수', '목', '금', '토', '일']" :key="`weekday-${item}`" :style="{
        color:index==6 ? '#c2131f' : '#9daab7'
      }">{{ item }}</div>
      <div class="flex auto align-items-center justify-content-center calendar-cell" v-for='(date, index) of dates' :key='`date${index}`'
        @click='!date.isBefore ? onItemClick(date) : null'
        :style="{color: date.isCurrentMonth && !date.isBefore ? '#595959' : '#D9D9D9' }"
      >
        {{ date.day }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props:{
    startTime:Number,
    endTime:String,
    calendarDisable:Boolean,
  },
  data () {
    return {
      selectedDate:null,
      isCalendarShow:false,
    }
  },
  computed: {
    dates () {
      let cursor = this.$moment(this.selectedDate)
      let currentMonth = cursor.month()
      let arr = []

      cursor.date(1).isoWeekday(1)

      for (let i = 0; i < 42; ++i) {
        arr.push({
          date: cursor.format('YYYY-MM-DD'),
          day: cursor.format('DD'),
          isCurrentMonth: cursor.month() == currentMonth,
          isBefore: cursor < this.$moment(this.startTime) ? true : false
        })
        cursor.add(1, 'day')
      }

      return arr
    }
  },
  methods:{
    onConfirm () {
      this.isCalendarShow = false
    },
    onItemClick (date) {
      this.selectedDate = date.date
      this.$emit('input', this.selectedDate)
      let that = this
      setTimeout(function(){
        that.onConfirm()
      },100)
    },
    onPrevClick () {
    this.selectedDate = this.$moment(this.selectedDate).add(-1, 'month').format('YYYY-MM')
    },
    onNextClick () {
      this.selectedDate = this.$moment(this.selectedDate).add(1, 'month').format('YYYY-MM')
    },
   },
  mounted(){
   this.selectedDate = this.startTime
  }
}
</script>
<style scoped>
.date-picker{
  background:#ffffff;
  box-shadow: 0 0 6px 0 rgba(33, 38, 46, 0.3);
  border-radius:2vw;
  margin:0 auto;
  width:90%;
  font-size:4vw;
  padding:1vw;
}
.calendar{
  background:#ffffff;
  box-shadow: 0 0 6px 0 rgba(33, 38, 46, 0.3);
  border-radius:1vw;
  margin:0 auto; 
  width:90%;
  padding:1vw 0;
}
.side-content{
  max-width: 10%;
  min-width:10%;
  color:#D8695E;
  font-size:6vw;
}
.calendar-cell{
  max-width: 14%;
  min-width:14%;
  font-size:4vw;
  margin:1vw 0;
}


</style>