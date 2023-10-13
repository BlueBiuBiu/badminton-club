<template>
  <div class="activity">
    <van-search
      :value="searchValue"
      shape="round"
      background="transparent"
      placeholder="请输入搜索关键词"
    />

    <van-tabs :active="1">
      <van-tab title="待报名">
        <activity-card v-for="item in 7" :key="item" @itemClick="itemClick(item)" />
      </van-tab>
      <van-tab title="报名中">
        <activity-card v-for="item in 7" :key="item" @itemClick="itemClick(item)" />
      </van-tab>
      <van-tab title="报名已截止">
        <activity-card v-for="item in 7" :key="item" @itemClick="itemClick(item)"
      /></van-tab>
      <van-tab title="进行中">
        <activity-card v-for="item in 7" :key="item" @itemClick="itemClick(item)"
      /></van-tab>
      <van-tab title="已结束">
        <activity-card v-for="item in 7" :key="item" @itemClick="itemClick(item)"
      /></van-tab>
    </van-tabs>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";

const searchValue = ref();

// 查看详情
const itemClick = (item: any) => {
  uni.navigateTo({ url: "/pages/activity/detail" });
};
</script>

<style lang="scss" scoped>
.activity {
}

/* 标签页 */
:deep(.van-tabs__scroll) {
  background-color: #393939;
}
:deep(.van-tab) {
  color: #b6b6b6;
}
:deep(.van-tab--active) {
  color: #ff8707;
}
:deep(.van-tabs__line) {
  background-color: #ff8707;
}
</style>
