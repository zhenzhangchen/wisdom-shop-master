<template>
  <view class="container">
    <!-- 店铺页面组件 -->
    <Page :items="items" />
  </view>
</template>

<script>
  import { setCartTabBadge } from '@/core/app'   // 加载购物车商品数量tabbadge
  import * as Api from '@/api/page'              
  import Page from '@/components/page'    // 首页布局，根据后端传的数据高度自定义

  export default {
    components: {
      Page
    },
    data() {
      return {
        // 页面参数
        options: {},
        // 页面属性
        // page: {},
        // 页面元素
        items: []
      }
    },

    /**
     * 生命周期函数--监听页面加载
     */
    onLoad(options) {
      // 当前页面参数
      this.options = options
      // 加载页面数据
      this.getPageData();
    },

    /**
     * 生命周期函数--监听页面显示
     */
    onShow() {
      // 更新购物车角标
      setCartTabBadge()
    },

    methods: {

      /**
       * 加载页面数据
       * @param {Object} callback
       */
      getPageData(callback) {
        const app = this
        const pageId = app.options.pageId || 0
        Api.detail(pageId)
          .then(result => {
			      console.log('加载首页',result)  
            // 设置页面数据
            const { data: { pageData } } = result
            app.items = pageData.items
          })
          .finally(() => callback && callback())
      },
    },

    /**
     * 下拉刷新
     */
    onPullDownRefresh() {
      // 获取首页数据
      this.getPageData(() => {
        uni.stopPullDownRefresh()
      })
    },

    /**
     * 分享当前页面
     */
    // onShareAppMessage() {
    //   const app = this
    //   const { page } = app
    //   return {
    //     title: page.params.share_title,
    //     path: "/pages/index/index?" + app.$getShareUrlParams()
    //   }
    // },

    /**
     * 分享到朋友圈
     * 本接口为 Beta 版本，暂只在 Android 平台支持，详见分享到朋友圈 (Beta)
     * https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/share-timeline.html
     */
    // onShareTimeline() {
    //   const app = this
    //   const { page } = app
    //   return {
    //     title: page.params.share_title,
    //     path: "/pages/index/index?" + app.$getShareUrlParams()
    //   }
    // }
  }
</script>

<style lang="scss" scoped>
  .container {
    background: #fff;
  }
</style>
