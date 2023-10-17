<script setup lang="ts">
import { onLaunch, onShow, onHide } from "@dcloudio/uni-app";
onLaunch(() => {
  /** 需要微信认证的小程序才能获取到用户的昵称 */
  uni.login({
    provider: "weixin",
    success: function (loginRes) {
      console.log("loginRes", loginRes);
      uni.authorize({
        scope: "scope.userInfo",
        success: function () {
          uni.getUserInfo({
            provider: "weixin",
            success: function (res) {
              uni.setStorageSync("userInfo", JSON.parse(res.rawData));
              console.log("res", res.rawData);
            },
            fail: function () {
              // 用户未授权，可以在这里处理未授权的逻辑
              console.log("用户未授权");
            },
          });
        },
      });
    },
    fail: function (err) {
      // 登录授权失败
      // err.code是错误码
    },
  });
});
onShow(() => {
  console.log("App Show");
});
onHide(() => {
  console.log("App Hide");
});
</script>

<style>
/*每个页面公共css */
page {
  background-color: #393939;
  color: #fff;
}
</style>
