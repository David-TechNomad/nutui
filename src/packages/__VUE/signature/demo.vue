<template>
  <div class="demo">
    <h2>{{ translate('basic') }}</h2>
    <div>
      <nut-signature ref="demo" custom-class="test" @confirm="confirm" @clear="clear" @start="start"></nut-signature>
      <img v-if="demoSignUrl" :src="demoSignUrl" class="demoSignUrl" />
    </div>
    <h2>{{ translate('title') }}</h2>
    <div>
      <nut-signature
        :line-width="4"
        stroke-style="green"
        @confirm="confirm2"
        @clear="clear2"
        @end="end"
      ></nut-signature>
      <img v-if="demoSignUrl2" :src="demoSignUrl2" class="demoSignUrl" />
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import { useTranslate } from '@/sites/assets/util/useTranslate';
const translate = useTranslate({
  'zh-CN': {
    basic: '基础用法',
    title: '修改颜色和签字粗细',
    tips: 'Tips: 点击确认按钮,下方显示签名图片'
  },
  'en-US': {
    basic: 'Basic Usage',
    title: 'Modify color and signature thickness',
    tips: 'Tips: click the confirm button, and the signature image is displayed below'
  }
});
const demoSignUrl = ref('');
const demoSignUrl2 = ref('');

const clear = () => {
  demoSignUrl.value = '';
  console.log('清除事件');
};
const clear2 = () => {
  demoSignUrl2.value = '';
  console.log('清除事件');
};
const confirm = (canvas: any, data: any) => {
  if (data === '') {
    console.log(canvas);
    return false;
  }
  demoSignUrl.value = data;
  console.log('图片地址', canvas, data);
};
const confirm2 = (canvas: any, data: any) => {
  if (data === '') {
    console.log(canvas);
    return false;
  }
  demoSignUrl2.value = data;
  console.log('图片地址', canvas, data);
};
const start = () => {
  console.log('签名开始');
};
const end = () => {
  console.log('签名结束');
};
</script>

<style lang="scss" scoped>
.demo {
  display: flex;
  flex-direction: column;

  .demo-tips {
    font-size: 12px;
    color: #666;
  }
}
</style>
