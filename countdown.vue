<template>
  <div class="countdown">
    <span class="active"
      v-if="timer === 0"
      v-text="defaultText"
      @click="run">
    ></span>
    <span v-else class="wait">{{waitText}} ({{timer}})s</span>
  </div>
</template>
<style lang="less">
.countdown{
  position: relative;
  width: 245px;
  text-align: center;
  &:after{
    content: '';
    position: absolute;
    top: -35px;
    left: 0;
    height: 102px;
    width: 1rpx;
    background-color: #dedede;
  }
  .active{
    color: #3d6dd8;
  }
  .wait{
    color: #94a3ae;
  }
}
</style>
<script>
export default {
  props: {
    time: {
      type: Number,
      default: 10
    },
    defaultText: {
      type: String,
      default: '获取验证码'
    },
    waitText: {
      type: String,
      default: '重新获取'
    },
    disable: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
      timer: 0
    }
  },
  watch: {},
  methods: {
    run() {
      this.$emit('run', '传给父组件')
    },
    start() {
      this.timer = this.time
      this.startTimer()
    },
    startTimer() {
      this.timer--
      if (this.timer > 0) {
        setTimeout(this.startTimer.bind(this), 1000)
      }
    }
  }
}
</script>
