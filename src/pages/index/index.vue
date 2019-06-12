<template>
  <div class="container" @click="clickHandle('test click', $event)">
    <!--<button open-type="getUserInfo">获取用户信息</button>-->
    <div class="userinfo">
      <img class="userinfo-avatar" v-if="userInfo.avatarUrl" :src="userInfo.avatarUrl" background-size="cover" />
      <div class="userinfo-nickname">
        <card :text="userInfo.nickName"></card>
      </div>
      <div class="usermotto">
        <div class="user-motto">
          <card :text="motto"></card>
        </div>
      </div>
      <a href="/pages/counter/main" class="counter" @click="show=true">点击内嵌H5</a>
      <div style="font-size: 12px;color: #a7a7a7;">
        如果出现不支持非业务域名，找到微信开发工具右上角，点击详情，勾选不校验合法域名 web-view即可
      </div>
    </div>

    <web-view src="https://www.baidu.com" v-if="show"></web-view>
  </div>
</template>

<script>
import card from '@/components/card'

export default {
  data () {
    return {
      motto: 'Hello World',
      userInfo: {},
      show:false
    }
  },

  components: {
    card
  },

  methods: {
    getUserInfo () {
      // 调用登录接口
      wx.login({
        success: () => {
          wx.getUserInfo({
            success: (res) => {
              this.userInfo = res.userInfo
            }
          })
        }
      })
    },
    clickHandle (msg, ev) {
      console.log('clickHandle:', msg, ev)
    }
  },

  created () {
    // 调用应用实例的方法获取全局数据
    this.getUserInfo()
  }
}
</script>

<style scoped>
.userinfo {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.userinfo-avatar {
  width: 128rpx;
  height: 128rpx;
  margin: 20rpx;
  border-radius: 50%;
}

.userinfo-nickname {
  color: #aaa;
}
.counter {
  display: inline-block;
  margin: 10px auto;
  padding: 5px 10px;
  color: blue;
  border: 1px solid blue;
}
</style>
