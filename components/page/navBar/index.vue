<template>
  <!-- 导航组 -->
  <view class="diy-navBar">
    <view class="data-list avg-sm-5">
      <view class="item-nav" v-for="(dataItem, index) in dataList" :key="index">
        <view class="nav-to" @click="onLink(dataItem.link)">
          <view class="item-image">
            <image class="image" mode="widthFix" :src="dataItem.imgUrl"></image>
          </view>
          <view class="item-text oneline-hide">{{ dataItem.text }}</view>
        </view>
      </view>
    </view>
  </view>
</template>

<script>
  import mixin from '../mixin'

  export default {
    name: "NavBar",
    /**
     * 组件的属性列表
     * 用于组件自定义设置
     */
    props: {
      // itemIndex: String,
      // itemStyle: Object,
      // params: Object,
      dataList: Array
    },

    mixins: [mixin],

    /**
     * 组件的方法列表
     * 更新属性和数据的方法与更新页面数据的方法类似
     */
    methods: {

    }

  }
</script>

<style lang="scss" scoped>
  .diy-navBar{
    background-color: #ffffff;
    color:#000000
  }
  .diy-navBar .data-list::after {
    clear: both;
    content: " ";
    display: table;
  }

  .item-nav {
    float: left;
    margin: 10px 0;
    text-align: center;

    .item-text {
      font-size: 26rpx;
    }

    .item-image {
      margin-bottom: 4px;
      font-size: 0;
    }

    .item-image .image {
      width: 88rpx;
      height: 88rpx;
    }

  }

  /* 分列布局 */

  // .diy-navBar .avg-sm-3>.item-nav {
  //   width: 33.33333333%;
  // }

  // .diy-navBar .avg-sm-4>.item-nav {
  //   width: 25%;
  // }

  .diy-navBar .avg-sm-5>.item-nav {
    width: 20%;
  }
</style>
