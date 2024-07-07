<template>
  <view class="homepage">
    <view class="eat-btn normal-btn" @tap="showEatSomething">吃点啥</view>
    <view class="more-btn normal-btn">还有啥</view>
  </view>
</template>

<script setup>
import Taro from '@tarojs/taro'
const showEatSomething = () => {
  console.log(123);
  Taro.navigateTo({
    url: '/pages/eatSomeThing/index'
  })
}
</script>

<style lang="scss">
.homepage {
  width: 100vw;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;

  .eat-btn {}

  .more-btn {
    margin-top: 30px;
    margin-bottom: 200px;
  }
}
</style>