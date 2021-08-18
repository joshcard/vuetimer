<template>
  <div>{{timerMinutes}} : {{timerSeconds}}</div>
</template>

<script>
export default {
  name: "Timer",
  props: {
    minutesLeft: {
      default: 2
    },
    secondsLeft: {
      default: 10
    },
  },
  data() {
    return {
      timerMinutes: this.minutesLeft,
      timerSeconds: this.secondsLeft,
    }
  },
  watch: {
    timerSeconds: {
      handler(value) {
        if (value > 0) {
          setTimeout(() => {
            this.timerSeconds--;
          }, 1000);
        }
      },
      immediate: true 
    },
    timerMinutes: {
      handler(value) {
        //this isn't setting the minute down one when the timerSeconds reaches 0
        if (value > 0 && this.timerSeconds === 0) {
          this.timerMinutes--;
        }
      },
      immediate: false 
    }
  }
}
</script>

<style>

</style>

