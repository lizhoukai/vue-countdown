# vue-countdown
- vue2.0 倒计时

## 参数
参数 | 说明 | 类型 | 默认值
---- |----|---- |----
time | 倒计时时间（秒）  | Number | 60
defaultText | 文字描述  | String | 获取验证码
waitText | 文字描述  | String | 重新获取
run | 函数  | Function | 父组件回调函数

## 使用
```js
<template>
  <countdown @run="sendAjax" ref="child"></countdown>
</template>
<script>
import countdown from 'components/countdown'

export default {
  components: {
    countdown
  },
  methods: {
    sendAjax(v) {
      this.$refs.child.start() // 根据$refs钩子，调用子组件方法
    }
  }
}
</script>
```

