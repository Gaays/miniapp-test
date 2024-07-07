<template>
  <view class="eat-some-thing">
    <view v-if="foodText" class="food-text">{{ foodText }}</view>
    <view :class="['normal-btn']" @tap="handleBtn">{{ btnText }}</view>
  </view>
</template>

<script setup>
import { ref } from 'vue'
import { foodList } from './data.ts'

const StartText = '开始'
const ReStartText = '重新开始'
const StopText = '停止'
const btnText = ref(StartText)
const foodText = ref('')
const randomFlag = ref(false)
let intervalIndex

const handleBtn = () => {
  // 初始状态
  if (!foodText.value) {
    randomFood()
    randomFlag.value = true
    btnText.value = StopText
  } else {
    if (randomFlag.value) {
      randomFlag.value = false
      clearInterval(intervalIndex)
      btnText.value = ReStartText
    } else {
      randomFlag.value = true
      randomFood()
      btnText.value = StopText
    }
  }

}

const randomFood = () => {
  intervalIndex = setInterval(() => {
    foodText.value = foodList[Math.floor(Math.random() * foodList.length)]
  }, 100);
}

</script>
<style lang="scss">
.eat-some-thing {
  width: 100vw;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;

  .start-btn {}

  .end-btn {
    margin-top: 40px;
  }
}
</style>