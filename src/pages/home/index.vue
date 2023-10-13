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
        <activity-card v-for="item in 7" :key="item" @itemClick="itemClick(item)" />
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
  console.log('-0');
  
  uni.navigateTo({ url: "/pages/activity/detail" });
};

// 查看更多
const viewMore = () => {
  uni.navigateTo({ url: "/pages/activity/index" });
};
</script>

<style lang="scss" scoped>
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

    .more {
      color: #fff;
      background-color: #ff8707;
      border-radius: 50rpx;
    }
  }
}
</style>
