<template>
  <view>
    <image
      class="banner"
      src="~@/assets/images/banner.png"
      mode="widthFix"
    ></image>
    <view class="operate">
      <view class="action" v-for="item in operation" @click="actionClick(item)">
        <image class="image" :src="item.image" mode="widthFix" />
        <text>{{ item.text }}</text>
      </view>
    </view>
    <view class=""></view>
    <view class="list"></view>
    <custom-tabbar :current-page="0" />
  </view>
</template>

<script setup lang="ts">
import { ref } from "vue";
import publishImage from "@/assets/images/publish.png"
import joinImage from "@/assets/images/join.png"
import activityImage from "@/assets/images/activity.png"

interface IOpreate {
  image: string,
  text: string,
  navigateUrl: string,
}

const operation = ref<IOpreate[]>([
  {
    image: publishImage,
    text: "发布活动",
    navigateUrl: '/pages/activity/index'
  },
  {
    image: joinImage,
    text: "加入社团",
    navigateUrl: ''
  },
  {
    image: activityImage,
    text: "社团活动",
    navigateUrl: ''
  },
]);

const actionClick = (item: IOpreate) => {
  uni.navigateTo({
    url: item.navigateUrl
  })
}
</script>

<style lang="less" scoped>
.banner {
  width: 100%;
}
.operate {
  display: flex;
  margin: 20rpx;
  background-color: #292929;
  border-radius: 20rpx;
  padding: 30rpx;
  justify-content: space-around;
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
</style>
