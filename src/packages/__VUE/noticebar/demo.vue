<template>
  <div class="demo full">
    <h2>{{ translate('basic') }}</h2>
    <nut-noticebar :text="translate('text')"></nut-noticebar>

    <h2>{{ translate('scrollable') }}</h2>
    <nut-noticebar :text="translate('textShort')" :scrollable="true"> </nut-noticebar>
    <p />
    <nut-noticebar :text="translate('text')" :scrollable="false"></nut-noticebar>

    <h2>{{ translate('mode') }}</h2>
    <nut-noticebar :close-mode="true" @click="closeFun">{{ translate('text') }} </nut-noticebar>
    <p />
    <nut-noticebar :close-mode="true" @click="closeFun">{{ translate('text') }} </nut-noticebar>
    <p />
    <nut-noticebar>
      <template #left-icon>
        <img
          src="https://img13.360buyimg.com/imagetools/jfs/t1/72082/2/3006/1197/5d130c8dE1c71bcd6/e48a3b60804c9775.png"
          style="width: 20px; height: 20px"
        />
      </template>
      <a href="https://www.jd.com">{{ translate('jd') }}</a>
    </nut-noticebar>

    <h2>{{ translate('multiline') }}</h2>
    <nut-noticebar :text="translate('text')" wrapable></nut-noticebar>

    <h2>{{ translate('vertical') }}</h2>

    <div class="interstroll-list">
      <nut-noticebar
        direction="vertical"
        :list="state.horseLamp1"
        :speed="10"
        :stand-time="1000"
        :close-mode="true"
        @click="go"
      ></nut-noticebar>
    </div>

    <h2>{{ translate('complexAm') }}</h2>
    <div class="interstroll-list">
      <nut-noticebar
        direction="vertical"
        :list="data1"
        :speed="10"
        :stand-time="2000"
        :complex-am="true"
      ></nut-noticebar>
    </div>
    <h2>{{ translate('customAm') }}</h2>
    <div class="interstroll-list">
      <nut-noticebar direction="vertical" :height="50" :speed="10" :stand-time="1000" :list="[]" @close="go">
        <div
          v-for="(item, index) in data1"
          :key="index"
          class="custom-item"
          :data-index="index"
          style="height: 50px; line-height: 50px"
          >{{ item }}</div
        >
      </nut-noticebar>
    </div>

    <h2>{{ translate('customRightIcon') }}</h2>
    <div class="interstroll-list">
      <nut-noticebar direction="vertical" :list="state.horseLamp1" :speed="10" :stand-time="1000">
        <template #right-icon>
          <Fabulous />
        </template>
      </nut-noticebar>
    </div>

    <h2>{{ translate('scrollEvent') }}</h2>
    <div class="interstroll-list">
      <nut-noticebar
        :text="`${translate('text')} - ${translate('scrollCount')}：[${state.acrossCount}]`"
        @across-end="onAcrossEnd"
      />
    </div>
  </div>
</template>

<script setup lang="ts">
import { reactive, ref } from 'vue';
import { Fabulous } from '@nutui/icons-vue';
import { useTranslate } from '@/sites/assets/util/useTranslate';

const translate = useTranslate({
  'zh-CN': {
    basic: '基础使用',
    scrollable: '滚动播放',
    mode: '通告栏--关闭模式',
    multiline: '多行展示',
    vertical: '垂直滚动',
    complexAm: '纵向--复杂滚动动画',
    customAm: '纵向--自定义滚动内容',
    customRightIcon: '纵向--自定义右侧图标',
    text: 'NutUI 是京东风格的移动端组件库，使用 Vue 语言来编写可以在 H5，小程序平台上的应用，帮助研发人员提升开发效率，改善开发体验。',
    textShort: 'NutUI 是移动端组件库',
    horseLamp: ['NoticeBar 公告栏', 'Cascader 级联选择', 'DatePicker 日期选择器', 'CheckBox 复选按钮'],
    jd: '京东商城',
    scrollCount: '滚动次数',
    scrollEvent: '横向 - 滚动结束事件'
  },
  'en-US': {
    basic: 'Basic Usage',
    scrollable: 'Scrollable',
    mode: 'Mode',
    multiline: 'Wrapable',
    vertical: 'Vertical Scroll',
    complexAm: 'Vertical Scroll Complex Animation',
    customAm: 'Vertical Scroll Custom Style',
    customRightIcon: 'Vertical Scroll Custom Right Icon',
    text: 'Nutui is a Jingdong style mobile terminal component library. It uses Vue language to write applications that can be used on H5 and applet platforms to help R & D personnel improve development efficiency and development experience.',
    textShort: 'Nutui is a mobile terminal component library.',
    horseLamp: ['NoticeBar', 'Cascader', 'DatePicker', 'CheckBox'],
    jd: 'Jingdong',
    scrollCount: 'scroll count',
    scrollEvent: 'across - scrolling end event'
  }
});
const state = reactive({
  horseLamp1: translate('horseLamp'),
  horseLamp2: translate('horseLamp'),
  horseLamp3: translate('horseLamp'),
  text: translate('text'),
  acrossCount: 0
});

const data1 = ref(['Noticebar 公告栏', 'Cascader 级联选择', 'DatePicker 日期选择器', 'CheckBox 复选按钮']);

const closeFun = () => {
  console.log('hello world');
};
const go = (item: any) => {
  console.log(item);
};

setTimeout(() => {
  data1.value = [
    'NutUI 是京东风格的移动端组件库，使用 Vue 语言来编写可以在 H5，小程序平台上的应用，帮助研发人员提升开发效率，改善开发体验。',
    '级联选择 Cascader',
    '日期选择器 DatePicker',
    '复选按钮 CheckBox'
  ];
}, 2000);

const onAcrossEnd = () => {
  state.acrossCount++;
  console.log('动画结束');
};
</script>

<style lang="scss" scoped>
.nut-theme-dark {
  .custom-item {
    color: $dark-color;
  }

  a {
    color: $dark-color;
  }
}

.demo {
  padding-bottom: 30px !important;

  .interstroll-list {
    background: rgba(251, 248, 220, 1);
    color: #d9500b;
  }

  .custom-item {
    width: 100%;
    text-overflow: ellipsis;
    white-space: nowrap;
    overflow: hidden;
  }
}
</style>
