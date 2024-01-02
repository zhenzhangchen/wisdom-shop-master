<template>
  <!-- 店铺公告 -->
  <view class="diy-notice" @click="onLink(params.link)">
    <u-notice-bar padding="10rpx 24rpx" :volume-icon="true" :autoplay="true"
      bg-color="#525252" color="#ffffff" :list="list"></u-notice-bar>
  </view>
</template>

<script>
  import mixin from '../mixin'

  export default {
    mixins: [mixin],

    data(){
      return{
        list:['GodFrey商城全新上线,更多新品等你来选~']
      }
    },

    /**
     * 组件的属性列表
     * 用于组件自定义设置
     */
    // props: {
    //   itemStyle: Object,
    //   params: Object
    // },
    /**
     * 组件的方法列表
     * 更新属性和数据的方法与更新页面数据的方法类似
     */
    methods: {
    }

  }
</script>

<style lang="scss" scoped>

</style>
