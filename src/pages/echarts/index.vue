<template>
  <div class="echarts-wrap">
    <swiper
      indicator-dots="indicatorDots"
      autoplay="true"
      interval="3000"
      duration="500"
      circular="true"
    >
      <block v-for="(item,index) in imgUrls" :key="index">
        <swiper-item>
          <img :src="item" alt="">
        </swiper-item>
      </block>
    </swiper>
    <a href="/pages/index/main" class="counter" @click="show=true">路由跳转(首页)</a>

  </div>
</template>

<script>
  // import $Message from '/static/dist/base/index'
  import {$Message} from '../../../static/dist/base/index'
  export default {

    data () {
      return {
        imgUrls: ["/static/image/index/pm1.png", "/static/image/index/pm10.png", "/static/image/index/pm25.png"],
      }
    },
    methods:{
      handleChange (e) {
        console.log(e);
        this.current= e.mp.detail.key;
      },
      handleDefault () {
        $Message({
          content: '这是一条普通提醒'
        });
      },
      handleSuccess () {
        $Message({
          content: '这是一条成功提醒',
          type: 'success'
        });
      },
      handleWarning () {
        $Message({
          content: '这是一条警告提醒',
          type: 'warning'
        });
      },
      handleError () {
        $Message({
          content: '这是一条错误提醒',
          type: 'error'
        });
      },
      handleDuration () {
        $Message({
          content: '我将在 5 秒后消失',
          duration: 5
        });
      }
    }
  }
</script>

<style scoped>

</style>
