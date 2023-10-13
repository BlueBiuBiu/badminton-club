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
        <van-uploader
          :file-list="form.image"
          accept="image"
          :max-count="1"
          @after-read="afterUpload"
        />
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
    <view class="row" @click="selectClick('signUpStartDateTime')">
      <text class="label">报名开始时间</text>
      <view class="operate" v-if="!form.signUpStartDateTime">
        <text>请选择</text>
        <image src="~@/assets/images/arrow-right.png" mode="widthFix" />
      </view>
      <view class="operate" v-else>
        <text>{{ formatDateTime(form.signUpStartDateTime) }}</text>
        <image src="~@/assets/images/date-icon.svg" mode="widthFix" />
      </view>
    </view>
    <view class="row" @click="selectClick('signUpEndDateTime')">
      <text class="label">报名结束时间</text>
      <view class="operate" v-if="!form.signUpEndDateTime">
        <text>请选择</text>
        <image src="~@/assets/images/arrow-right.png" mode="widthFix" />
      </view>
      <view class="operate" v-else>
        <text>{{ formatDateTime(form.signUpEndDateTime) }}</text>
        <image src="~@/assets/images/date-icon.svg" mode="widthFix" />
      </view>
    </view>
    <view class="row" @click="selectClick('activityStartDataTime')">
      <text class="label">活动开始时间</text>
      <view class="operate" v-if="!form.activityStartDataTime">
        <text>请选择</text>
        <image src="~@/assets/images/arrow-right.png" mode="widthFix" />
      </view>
      <view class="operate" v-else>
        <text>{{ formatDateTime(form.activityStartDataTime) }}</text>
        <image src="~@/assets/images/date-icon.svg" mode="widthFix" />
      </view>
    </view>
    <view class="row" @click="selectClick('activityEndDataTime')">
      <text class="label">活动结束时间</text>
      <view class="operate" v-if="!form.activityEndDataTime">
        <text>请选择</text>
        <image src="~@/assets/images/arrow-right.png" mode="widthFix" />
      </view>
      <view class="operate" v-else>
        <text>{{ formatDateTime(form.activityEndDataTime) }}</text>
        <image src="~@/assets/images/date-icon.svg" mode="widthFix" />
      </view>
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

    <!-- 遮罩层 -->
    <view
      v-if="dateTimePickerHeight > 0"
      class="mask"
      @click="dateTimePickerHeight = 0"
    ></view>
    <van-datetime-picker
      :style="{ height: `${dateTimePickerHeight}rpx` }"
      class="datetime-picker"
      type="datetime"
      :value="form[currentField] || new Date().getTime()"
      :formatter="formatter"
      @confirm="confirmTime"
      @cancel="dateTimePickerHeight = 0"
    />

    <view class="publish">
      <button class="publish-btn" @click="submit">发布</button>
    </view>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import dayjs from 'dayjs'
type fieldType =
  | "signUpStartDateTime"
  | "signUpEndDateTime"
  | "activityStartDataTime"
  | "activityEndDataTime";

const dateTimePickerHeight = ref(0);
const currentField = ref<fieldType>("signUpStartDateTime");
const form = ref({
  activityName: "",
  activityArea: "",
  image: [],
  activityIntrodue: "",
  signUpStartDateTime: null,
  signUpEndDateTime: null,
  activityStartDataTime: null,
  activityEndDataTime: null,
  numberLimit: 0,
  contactPeople: "",
  phoneNumber: "",
});

// 点击时间选择
const selectClick = (field: fieldType) => {
  dateTimePickerHeight.value = 550;
  currentField.value = field;
};

// 确定时间
const confirmTime = (e: any) => {
  console.log(e.detail);
  form.value[currentField.value] = e.detail;
  dateTimePickerHeight.value = 0;
};

// 格式化时间
const formatDateTime = (value: number) => {
  return dayjs(value).format("YYYY-MM-DD HH:mm")
}

const formatter = (
  type: "year" | "month" | "day" | "hour" | "minute",
  value: number
) => {
  switch (type) {
    case "year":
      return `${value}年`;
    case "month":
      return `${value}月`;
    case "day":
      return `${value}日`;
    case "hour":
      return `${value}时`;
    case "minute":
      return `${value}分`;
    default:
      return value;
  }
};

// 上传封面后
const afterUpload = (e: any) => {
  console.log(e.detail);
};

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

  .mask {
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 999;
    background-color: rgba(0, 0, 0, 0.6);
  }

  .datetime-picker {
    position: fixed;
    width: 100%;
    height: 0;
    bottom: 0;
    z-index: 9999;
    transition: height 0.3s ease;
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

:deep(.van-uploader__upload) {
  background-color: #393939;
}

/* 时间日期选择器 */
:deep(.van-picker),
:deep(.van-picker__toolbar) {
  background-color: #393939;
  border-top-left-radius: 30rpx;
  border-top-right-radius: 30rpx;
}
:deep(.van-picker__toolbar) {
  background-color: #393939;
}

:deep(.van-picker__confirm) {
  color: #ff8707;
}
:deep(.van-picker__columns) {
  background-color: #3f3f3f;
}
:deep(.van-picker__mask) {
  display: none;
}
:deep(.van-picker-column__item) {
  color: #797979;
}
:deep(.van-picker-column__item--selected) {
  color: #fff;
}
</style>
