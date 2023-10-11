import { onMounted } from 'vue';
<template>
  <view class="popup" :style="{ height: `${currentHeight}rpx` }">
    <view class="title">
      <text>{{ title }}</text>
      <image
        class="close"
        src="~@/assets/images/close.png"
        mode="widthFix"
        @click="closePopup"
      />
    </view>
    <slot></slot>
  </view>
</template>

<script setup lang="ts">
import { onMounted, ref } from "vue";

const props = withDefaults(
  defineProps<{
    height: number;
    title: string;
  }>(),
  {
    height: 600,
    title: "",
  }
);

const currentHeight = ref(0);

onMounted(() => {
  console.log("----------");

  currentHeight.value = props.height;
});

const closePopup = () => {};
</script>

<style lang="less" scoped>
.popup {
  position: fixed;
  width: 100%;
  height: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: #3f3f3f;
  border-top-left-radius: 30rpx;
  border-top-right-radius: 30rpx;

  transition: height 1ss ease-in;

  .title {
    width: 100%;
    height: 96rpx;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #393939;
    font-size: 36rpx;
    border-top-left-radius: 30rpx;
    border-top-right-radius: 30rpx;
    position: relative;
    .close {
      width: 40rpx;
      position: absolute;
      right: 20rpx;
    }
  }
}
</style>
