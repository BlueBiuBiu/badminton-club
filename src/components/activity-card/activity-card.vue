<template>
  <view class="item" @click="itemClick">
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
</template>

<script setup lang="ts">
const emits = defineEmits(["itemClick"]);

const itemClick = () => {
  emits("itemClick");
};
</script>

<style lang="scss" scoped>
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
</style>
