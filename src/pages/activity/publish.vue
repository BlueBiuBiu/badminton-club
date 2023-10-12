<template>
  <div class="publish">
    <view class="row">
      <text class="label">活动名称</text>
      <input
        type="text"
        v-model="form.activityName"
        placeholder="请输入"
        placeholder-style="color:#ffffff"
      />
    </view>
    <view class="row">
      <text class="label">活动地点</text>
      <input
        type="text"
        v-model="form.activityArea"
        placeholder="请输入"
        placeholder-style="color:#ffffff"
      />
    </view>
    <view class="row-vertical">
      <text class="label">上传封面图片</text>
      <view class="picker">
        <uni-file-picker fileMediatype="image" limit="1"></uni-file-picker>
      </view>
    </view>
    <view class="row-vertical">
      <text class="label">活动介绍</text>
      <textarea
        v-model="form.activityIntrodue"
        placeholder="请输入..."
        placeholder-style="color:#ffffff"
      />
    </view>
    <view class="row">
      <text class="label">报名时间</text>
      <uni-datetime-picker
        v-model="form.signUpDateTime"
        type="datetimerange"
        rangeSeparator="至"
      />
    </view>
    <view class="row">
      <text class="label">活动时间</text>
      <uni-datetime-picker
        v-model="form.activityDataTime"
        type="datetimerange"
        rangeSeparator="至"
      />
    </view>
    <view class="row">
      <text class="label">可参加人数（人）</text>
      <input
        type="number"
        v-model="form.numberLimit"
        placeholder="请输入"
        placeholder-style="color:#ffffff"
      />
    </view>
    <view class="row">
      <text class="label">活动联系人</text>
      <input
        type="text"
        v-model="form.contactPeople"
        placeholder="请输入"
        placeholder-style="color:#ffffff"
      />
    </view>
    <view class="row">
      <text class="label">联系电话</text>
      <input
        type="tel"
        v-model="form.phoneNumber"
        placeholder="请输入"
        placeholder-style="color:#ffffff"
      />
    </view>

    <view class="publish">
      <button class="publish-btn" @click="submit">发布</button>
    </view>
  </div>
</template>

<script setup lang="ts">
import uniDatetimePicker from "@/components/uni-datetime-picker/uni-datetime-picker.vue";
import uniFilePicker from "@/components/uni-file-picker/uni-file-picker.vue";
import { ref } from "vue";

const form = ref({
  activityName: "",
  activityArea: "",
  image: [],
  activityIntrodue: "",
  signUpDateTime: "",
  activityDataTime: "",
  numberLimit: 0,
  contactPeople: "",
  phoneNumber: "",
});

const submit = () => {
  console.log("form", form.value);
};
</script>

<style lang="scss" scoped>
.publish {
  width: 100%;
  height: 100%;
  box-sizing: border-box;
  padding-bottom: 120rpx;

  .row {
    display: flex;
    align-items: center;
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
  }

  .row-vertical {
    background-color: #292929;
    padding: 20rpx;
    font-size: 28rpx;
    margin-bottom: 4rpx;

    .label {
      color: gray;
      &::before {
        content: "*";
        color: #ff8707;
      }
    }

    textarea {
      box-sizing: border-box;
      width: 100%;
      margin-top: 20rpx;
      background-color: #393939;
      border-radius: 6rpx;
      padding: 20rpx;
    }

    .picker {
      margin-top: 20rpx;
      width: 500rpx;
    }
  }

  .publish {
    position: fixed;
    left: 0;
    right: 0;
    bottom: 0;
    height: 120rpx;
    padding: 20rpx;
    background-color: #393939;
    z-index: 999;
    .publish-btn {
      color: #fff;
      background-color: #ff8707;
      border-radius: 50rpx;
    }
  }
}
</style>
