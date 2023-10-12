<template>
  <div class="detail">
    <view class="banner">
      <image
        class="banner-image"
        src="~@/assets/images/banner.png"
        mode="widthFix"
      ></image>
      <view class="banner-tip">
        <view class="content">
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
            <text>报名日期：</text>
            <text>2023.10.09 8:00 ~ 2023.10.14 23:59</text>
          </view>
          <view>
            <image
              class="icon"
              src="~@/assets/images/clock-icon.png"
              mode="widthFix"
            />
            <text>活动日期：</text>
            <text>2023.10.09 8:00 ~ 2023.10.14 23:59</text>
          </view>
          <view>
            <image
              class="icon"
              src="~@/assets/images/people-icon.png"
              mode="widthFix"
            />
            <text>已报名：</text>
            <text><text class="currentNum">112</text> /500</text>
          </view>
        </view>
      </view>
    </view>
    <view class="introduce">
      <view class="content">
        <text class="title">活动介绍</text>
        <view class="desc">
          羽毛球赛火热来袭！这里有激烈的对抗，也有友谊的碰撞。无论你是新手还是高手，只要你热爱羽毛球，这里就是你展现自我、挑战自我的舞台。让我们一起挥舞球拍，享受比赛，感受运动的魅力！
        </view>
      </view>
      <view class="contact">
        <view>
          <image
            class="contact-icon"
            src="~@/assets/images/detail-position.png"
            mode="widthFix"
          />
          <text class="label">活动地址：</text>
          <text>广东省湛江市机电学校</text>
        </view>
        <view>
          <image
            class="contact-icon"
            src="~@/assets/images/detail-contact.png"
            mode="widthFix"
          />
          <text class="label">活动联系人：</text>
          <text>潘星佑 | 13344445555</text>
        </view>
      </view>
      <view class="people">
        <view @click="viewPeople">
          <text class="title">报名成员(112)</text>
          <image
            class="arrow-right"
            src="~@/assets/images/arrow-right.png"
            mode="widthFix"
          />
        </view>
        <view class="people-list">
          <scroll-view class="scroll-people-list" scroll-x="true">
            <image
              class="avatar"
              src="~@/assets/images/avatar.jpg"
              mode="widthFix"
            />
            <image
              class="avatar"
              src="~@/assets/images/avatar.jpg"
              mode="widthFix"
            /><image
              class="avatar"
              src="~@/assets/images/avatar.jpg"
              mode="widthFix"
            /><image
              class="avatar"
              src="~@/assets/images/avatar.jpg"
              mode="widthFix"
            /><image
              class="avatar"
              src="~@/assets/images/avatar.jpg"
              mode="widthFix"
            /><image
              class="avatar"
              src="~@/assets/images/avatar.jpg"
              mode="widthFix"
            /><image
              class="avatar"
              src="~@/assets/images/avatar.jpg"
              mode="widthFix"
            /><image
              class="avatar"
              src="~@/assets/images/avatar.jpg"
              mode="widthFix"
            /><image
              class="avatar"
              src="~@/assets/images/avatar.jpg"
              mode="widthFix"
            /><image
              class="avatar"
              src="~@/assets/images/avatar.jpg"
              mode="widthFix"
            /><image
              class="avatar"
              src="~@/assets/images/avatar.jpg"
              mode="widthFix"
            /><image
              class="avatar"
              src="~@/assets/images/avatar.jpg"
              mode="widthFix"
            /><image
              class="avatar"
              src="~@/assets/images/avatar.jpg"
              mode="widthFix"
            /><image
              class="avatar"
              src="~@/assets/images/avatar.jpg"
              mode="widthFix"
            /><image
              class="avatar"
              src="~@/assets/images/avatar.jpg"
              mode="widthFix"
            /><image
              class="avatar"
              src="~@/assets/images/avatar.jpg"
              mode="widthFix"
            /><image
              class="avatar"
              src="~@/assets/images/avatar.jpg"
              mode="widthFix"
            />
            <image
              class="avatar"
              src="~@/assets/images/avatar.jpg"
              mode="widthFix"
            />
            <image
              class="avatar"
              src="~@/assets/images/avatar.jpg"
              mode="widthFix"
            />
            <image
              class="avatar"
              src="~@/assets/images/avatar.jpg"
              mode="widthFix"
            />
            <image
              class="avatar"
              src="~@/assets/images/avatar.jpg"
              mode="widthFix"
            />
          </scroll-view>
        </view>
      </view>
    </view>

    <view class="sign-up">
      <button class="sign-btn" @click="toSignUp">我要报名</button>
    </view>

    <!-- 底部弹出层组件 -->
    <popup title="报名成员" v-if="popupVisible" @close="popupVisible = false">
      <scroll-view class="scroll" scroll-y="true">
        <view class="table">
          <view class="tr">
            <view class="th">序号</view>
            <view class="th">头像</view>
            <view class="th">昵称</view>
            <view class="th">报名时间</view>
          </view>
          <view class="tr" v-for="i in 20">
            <view class="td">齐安</view>
            <view class="td">18</view>
            <view class="td">16102</view>
            <view class="td">2023/10/09 15:08</view>
          </view>
        </view>
      </scroll-view>
    </popup>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";

const popupVisible = ref(false);
const viewPeople = () => {
  popupVisible.value = true;
};

// 报名
const toSignUp = () => {};
</script>

<style lang="scss" scoped>
.detail {
  .banner {
    position: relative;
    .banner-image {
      width: 100%;
    }
    .banner-tip {
      position: absolute;
      top: 0;
      right: 0;
      bottom: 0;
      left: 0;
      background-color: rgba(0, 0, 0, 0.65);

      .content {
        width: 75%;
        color: #fff;
        font-size: 24rpx;
        margin-top: 50rpx;
        margin-left: 20rpx;
        .top {
          display: flex;
          justify-content: space-between;
          align-items: center;
          margin-bottom: 30rpx;

          .title {
            font-size: 32rpx;
            font-weight: 600;
          }
          .text {
            display: inline-flex;
            justify-content: center;
            align-items: center;
            padding: 4rpx 26rpx;
            border: 1px solid;
            border-radius: 4rpx;
          }

          ~ view {
            display: flex;
            align-items: center;
            margin-bottom: 20rpx;
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
  }

  .introduce {
    margin: 20rpx 0;
    .content {
      margin-bottom: 20rpx;
      .title {
        margin: 20rpx;
        font-size: 32rpx;
        font-weight: bold;
        position: relative;
        padding-left: 16rpx;

        &::before {
          content: "";
          display: inline-block;
          width: 6rpx;
          height: 30rpx;
          background-color: #ff8707;
          position: absolute;
          left: 0;
          top: 8rpx;
        }
      }

      .desc {
        padding: 20rpx;
        line-height: 50rpx;
      }
    }
    .contact {
      background-color: #292929;
      padding: 20rpx;
      font-size: 28rpx;
      margin-bottom: 20rpx;
      .contact-icon {
        width: 40rpx;
        margin-right: 20rpx;
      }
      .label {
        width: 170rpx;
        flex-shrink: 0;
      }
      view {
        display: flex;

        &:first-child {
          margin-bottom: 20rpx;
          .label {
            width: 140rpx;
            flex-shrink: 0;
          }
        }
      }
    }

    .people {
      background-color: #292929;
      view {
        display: flex;
        align-items: center;
        justify-content: space-between;
        .title {
          margin: 20rpx;
          font-size: 32rpx;
          font-weight: bold;
          position: relative;
          padding-left: 16rpx;

          &::before {
            content: "";
            display: inline-block;
            width: 6rpx;
            height: 30rpx;
            background-color: #ff8707;
            position: absolute;
            left: 0;
            top: 8rpx;
          }
        }
        .arrow-right {
          width: 36rpx;
          margin-right: 16rpx;
        }
      }
      .people-list {
        .scroll-people-list {
          display: flex;
          white-space: nowrap;
          padding: 30rpx 0;

          .avatar {
            width: 10%;
            border-radius: 50%;
            margin-left: 50rpx;

            &:last-child {
              margin-right: 50rpx;
            }
          }
        }
      }
    }
  }

  .sign-up {
    position: fixed;
    left: 0;
    right: 0;
    bottom: 0;
    padding: 20rpx;
    background-color: #393939;
    z-index: 1;
    .sign-btn {
      color: #fff;
      background-color: #ff8707;
      border-radius: 50rpx;
    }
  }

  .table {
    display: table;
    width: 100%;
    border-collapse: collapse;
    background-color: #3f3f3f;
    .tr {
      display: table-row;

      .th {
        display: table-cell;
        font-weight: bold;
        padding: 10rpx;
        color: #8e8e8e;
        text-align: center;
        vertical-align: middle;
      }
      .td {
        display: table-cell;
        padding: 10rpx;
        text-align: center;
        vertical-align: middle;
      }
    }
  }

  .scroll {
    width: 100%;
    height: 500rpx;
    position: relative;

    .table {
      display: table;
      border-collapse: collapse;
      width: 100%;
      height: 100%;

      .tr {
        display: table-row;
        text-align: center;
        vertical-align: middle;
        .th {
          display: table-cell;
          font-weight: bold;
          padding: 10rpx;
          color: #8e8e8e;
          background-color: #3f3f3f;

          position: sticky;
          top: 0; /* 列首永远固定在头部  */
        }

        .td {
          display: table-cell;
          padding: 10rpx;
        }
      }
    }
  }
}
</style>
