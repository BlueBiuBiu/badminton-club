<template>
  <view class="mine">
    <view class="user-info">
      <image class="avatar" :src="userInfo?.avatarUrl" mode="widthFix" />
      <view>
        <text>{{ userInfo?.nickName }}</text>
        <image
          class="sex-icon"
          v-if="userInfo?.gender === 0"
          src="~@/assets/images/sex-man.png"
          mode="widthFix"
        />
        <image
          v-else
          class="sex-icon"
          src="~@/assets/images/sex-women.png"
          mode="widthFix"
        />
      </view>
    </view>

    <view class="sign-up">
      <view>
        <text class="text">我的报名</text>
        <image
          class="arrow-right"
          src="~@/assets/images/arrow-right.png"
          mode="widthFix"
        />
      </view>
      <view class="list">
        <van-empty
          class="custom-image"
          image="https://img.yzcdn.cn/vant/custom-empty-image.png"
          description="暂无报名"
        />
      </view>
    </view>

    <view class="operate">
      <view
        class="item"
        v-for="item in operateList"
        :key="item.label"
        @click="itemClick(item)"
      >
        <view>
          <image class="icon" :src="item.icon" mode="widthFix" />
          <text>{{ item.label }}</text>
        </view>
        <image
          class="icon"
          src="~@/assets/images/arrow-right.png"
          mode="widthFix"
        />
      </view>
    </view>
  </view>
  <custom-tabbar class="custom-tabbar" :current-page="2" />
</template>

<script setup lang="ts">
import { onMounted, ref } from "vue";
import joinIcon from "@/assets/images/join.png";
import publishIcon from "@/assets/images/publish.png";
import activityIcon from "@/assets/images/activity.png";
import detailContactIcon from "@/assets/images/detail-contact.png";
import positionIcon from "@/assets/images/detail-position.png";

const userInfo = ref();
const operateList = ref([
  {
    label: "社团成员",
    icon: joinIcon,
    navigator: "",
  },
  {
    label: "我的发布",
    icon: publishIcon,
    navigator: "",
  },
  {
    label: "我的成绩",
    icon: activityIcon,
    navigator: "",
  },
  {
    label: "我的审核",
    icon: detailContactIcon,
    navigator: "",
  },
  {
    label: "我的缴费",
    icon: positionIcon,
    navigator: "",
  },
]);

const itemClick = (item: any) => {
  console.log(item);
};

onMounted(() => {
  const res = uni.getStorageSync("userInfo");
  if (res) {
    userInfo.value = res;
  }
});
</script>

<style lang="scss" scoped>
.custom-tabbar {
  width: 100%;
  height: 100%;
}
.mine {
  padding: 20rpx;
  padding-bottom: 180rpx;
  .user-info {
    display: flex;
    background-color: #292929;
    padding: 20rpx;
    .avatar {
      width: 100rpx;
      border-radius: 50%;
      margin-right: 20rpx;
    }

    text {
      font-weight: 600;
    }

    .sex-icon {
      width: 26rpx;
      margin-left: 10rpx;
    }
  }

  .sign-up {
    padding: 20rpx;
    background-color: #292929;
    margin-top: 20rpx;
    border-radius: 10rpx;

    view {
      display: flex;
      align-items: center;
      justify-content: space-between;
      .text {
        font-weight: bold;
      }
      .arrow-right {
        width: 30rpx;
        margin-right: 16rpx;
      }
    }

    .list {
      display: flex;
      justify-content: center;
    }
  }

  .operate {
    background-color: #292929;
    margin-top: 20rpx;
    padding: 20rpx;
    border-radius: 20rpx;
    .item {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 20rpx 0;
      &:not(:last-child) {
        border-bottom: 2rpx solid #393939;
      }
      view {
        display: flex;
        align-items: center;
        font-size: 26rpx;
        .icon {
          margin-right: 20rpx;
          width: 40rpx;
        }
      }
      .icon {
        width: 30rpx;
      }
    }
  }
}
</style>
