<template>
  <div class="join">
    <view class="row">
      <text class="label">昵称</text>
      <input
        type="text"
        placeholder="请输入"
        placeholder-style="color:#ffffff"
      />
    </view>
    <view class="row">
      <text class="label">手机号</text>
      <input
        type="text"
        placeholder="请输入"
        placeholder-style="color:#ffffff"
      />
    </view>

    <view class="submit">
      <button class="submit-btn" @click="submit">提交</button>
    </view>
  </div>
</template>

<script setup lang="ts">
const submit = () => {};
</script>

<style lang="scss" scoped>
.join {
  .row {
    display: flex;
    align-items: center;
    justify-content: space-between;
    background-color: #292929;
    padding: 20rpx;
    font-size: 28rpx;
    margin-bottom: 4rpx;

    .label {
      color: gray;
      margin-right: 20rpx;
      &::before {
        content: "*";
        color: #ff8707;
      }
    }

    input {
      text-align: right;
      flex: 1;
    }

    .operate {
      display: flex;
      align-items: center;
      image {
        width: 34rpx;
        margin-left: 6rpx;
      }
    }
  }

  .submit {
    position: fixed;
    left: 0;
    right: 0;
    bottom: 0;
    padding: 20rpx;
    background-color: #393939;
    z-index: 999;
    .submit-btn {
      color: #fff;
      background-color: #ff8707;
      border-radius: 50rpx;
    }
  }
}
</style>
