<template>
  <view class="home">
    <image
      class="banner"
      src="~@/assets/images/banner.png"
      mode="widthFix"
    ></image>
    <view class="content">
      <view class="operate">
        <view
          class="action"
          v-for="item in operation"
          :key="item.navigateUrl"
          @click="actionClick(item)"
        >
          <image class="image" :src="item.image" mode="widthFix" />
          <text>{{ item.text }}</text>
        </view>
      </view>

      <!-- 活动列表 -->
      <view class="tab">最新活动</view>
      <view class="list">
        <view class="item" v-for="item in 7" :key="item" @click="itemClick(item)">
          <view class="left">
            <image
              class="cover"
              src="~@/assets/images/cover.png"
              mode="scaleToFill"
            />
            <view class="process">报名中</view>
          </view>
          <view class="right">
            <view class="top">
              <text class="title">羽毛球比赛</text>
              <text class="text">羽毛球</text>
            </view>
            <view>
              <image
                class="icon"
                src="~@/assets/images/clock-icon.png"
                mode="widthFix"
              />
              <text>10/09 8:00~10/14 23:59</text>
            </view>
            <view>
              <image
                class="icon"
                src="~@/assets/images/people-icon.png"
                mode="widthFix"
              />
              <text><text class="currentNum">112</text> /500</text>
            </view>
            <view>
              <image
                class="icon"
                src="~@/assets/images/position-icon.png"
                mode="widthFix"
              />
              <text>羽毛球比赛</text>
            </view>
          </view>
        </view>
        <button class="more" @click="viewMore">查看更多</button>
      </view>
    </view>
    <custom-tabbar :current-page="0" />
  </view>
</template>

<script setup lang="ts">
import { ref } from "vue";
import publishImage from "@/assets/images/publish.png";
import joinImage from "@/assets/images/join.png";
import activityImage from "@/assets/images/activity.png";

interface IOpreate {
  image: string;
  text: string;
  navigateUrl: string;
}

const operation = ref<IOpreate[]>([
  {
    image: publishImage,
    text: "发布活动",
    navigateUrl: "/pages/activity/publish",
  },
  {
    image: joinImage,
    text: "加入社团",
    navigateUrl: "/pages/activity/join",
  },
  {
    image: activityImage,
    text: "社团活动",
    navigateUrl: "/pages/activity/index",
  },
]);

const actionClick = (item: IOpreate) => {
  uni.navigateTo({
    url: item.navigateUrl,
  });
};

// 查看详情
const itemClick = (item: any) => {
  uni.navigateTo({ url: "/pages/activity/detail" });
};

// 查看更多
const viewMore = () => {
  uni.navigateTo({ url: "/pages/activity/index" });
};
</script>

<style lang="less" scoped>
.home {
  .banner {
    width: 100%;
  }
  .content {
    margin: 20rpx;
  }
  .operate {
    display: flex;
    background-color: #292929;
    border-radius: 20rpx;
    padding: 30rpx;
    justify-content: space-around;
    margin-bottom: 20rpx;
    .action {
      display: flex;
      align-items: center;
      flex-direction: column;
      .image {
        width: 80rpx;
        margin-bottom: 10rpx;
      }
    }
  }

  .tab {
    font-size: 36rpx;
    margin-top: 20rpx;
    font-weight: bold;
    color: #d7d7d7;
    margin-bottom: 20rpx;
  }
  .list {
    padding-bottom: 170rpx;
    .item {
      display: flex;
      justify-content: space-between;
      background-color: #292929;
      padding: 30rpx;
      border-radius: 20rpx;
      margin-bottom: 20rpx;
      .left {
        width: 35%;
        position: relative;
        .cover {
          width: 100%;
          height: 100%;
          border-radius: 10rpx;
        }

        .process {
          position: absolute;
          padding: 4rpx 16rpx;
          top: 0;
          right: 0;
          font-size: 22rpx;
          background-color: #ff8707;
          border-bottom-left-radius: 10rpx;
          border-top-right-radius: 10rpx;
        }
      }

      .right {
        width: 60%;
        color: #fff;
        font-size: 24rpx;
        .top {
          display: flex;
          justify-content: space-between;
          align-items: center;
          margin-bottom: 10rpx;
          .title {
            font-size: 32rpx;
          }
          .text {
            display: inline-flex;
            justify-content: center;
            align-items: center;
            width: 120rpx;
            height: 50rpx;
            color: #ff8707;
            border-radius: 4rpx;
            background-color: #3f3326;
          }

          ~ view {
            display: flex;
            align-items: center;
            margin-bottom: 10rpx;
          }
        }
        .icon {
          width: 30rpx;
          margin-right: 6rpx;
        }
        .currentNum {
          color: #ff8707;
        }
      }
    }

    .more {
      color: #fff;
      background-color: #ff8707;
      border-radius: 50rpx;
    }
  }
}
</style>
