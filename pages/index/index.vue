<template>
  <view class="content">
    <u-navbar height="50" placeholder bgColor="#4989ff">
      <view slot="left" style="color: white;">{{ userSite }}</view>
    </u-navbar>
    <view style="width: 100%; background-color: #4987ff; margin-top: -2px; border-radius:0 0 50rpx 50rpx;  ">
      <u-cell-group>
        <u-cell rightIconStyle="color:white">
          <view slot="title">
            <view class="userInfo">
              <view style="height: 190rpx; display: flex; flex-direction: column; justify-content: center;"><u-avatar :src="userAvater" size="80"></u-avatar></view>
              <view style="height: 190rpx;display: flex;  flex-direction: column; justify-content: space-evenly; margin-left: 20rpx; ">
                <view style="display: flex;">
                  <view style="font-size: 40rpx;margin-right: 10rpx;">张三</view>
                  <view style="text-align: center; background-color: #7aafff;width: 100rpx;height: 50rpx;line-height: 50rpx; border-radius: 30%;margin-top: 4rpx;">站长</view>
                </view>
                <view style="font-size: 30rpx;">id:115213</view>
              </view>
            </view>
          </view>
          <view slot="right-icon"><u-icon name="arrow-right" color="#ffffff" size="28"></u-icon></view>
        </u-cell>
      </u-cell-group>
    </view>
    <view class="middlePanel">
      <view class="">
        <view class="">2023-07</view>
        <view class="">8373.8元</view>
      </view>
      <view class="">
        <view class="">今日</view>
        <view>278.5元</view>
      </view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      title: 'Hello',
      userSite: '万州加油站',
      userAvater: require('../../static/logo.png')
    };
  },
  onLoad() {},
  methods: {
    rightClick() {}
  }
};
</script>

<style scoped lang="scss">
.middlePanel {
  position: absolute;
  top: 400rpx;
  left: 50%;
  transform: translateX(-50%);
  background-color: #fff;
  width: 90%;
  height: 190rpx;
  border-radius: 20rpx;
}

.userInfo {
  display: flex;
  height: 290rpx;
  color: #fff;
}
.content {
  position: relative;
  background-color: #f4f4f4;
  height: 100vh;
}
</style>
