<template>
  <Demo class="full">
    <h2>基础用法</h2>
    <nut-cell>
      <nut-progress percentage="30" />
    </nut-cell>

    <h2>设置颜色高度</h2>
    <nut-cell>
      <nut-progress percentage="30" stroke-color="rgba(250,44,25,0.47)" stroke-width="20" text-color="red" />
    </nut-cell>

    <h2>设置百分比不显示</h2>
    <nut-cell>
      <nut-progress percentage="50" :show-text="false" stroke-height="24" />
    </nut-cell>

    <h2>设置百分比内显</h2>
    <nut-cell>
      <nut-progress percentage="60" :text-inside="true" />
    </nut-cell>

    <h2>设置百分比内显自定义内容</h2>
    <nut-cell>
      <nut-progress percentage="60" :text-inside="true">
        <img
          src="https://img11.360buyimg.com/imagetools/jfs/t1/137646/13/7132/1648/5f4c748bE43da8ddd/a3f06d51dcae7b60.png"
          width="30"
          height="30"
        />
      </nut-progress>
    </nut-cell>

    <h2>设置自定义尺寸</h2>
    <nut-cell>
      <nut-progress percentage="30" :text-inside="true" size="small"> </nut-progress>
    </nut-cell>
    <nut-cell>
      <nut-progress percentage="50" :text-inside="true" size="base"> </nut-progress>
    </nut-cell>
    <nut-cell>
      <nut-progress percentage="70" :text-inside="true" size="large"> </nut-progress>
    </nut-cell>

    <h2>设置状态显示</h2>
    <nut-cell>
      <nut-progress
        percentage="30"
        stroke-color="linear-gradient(270deg, rgba(18,126,255,1) 0%,rgba(32,147,255,1) 32.815625%,rgba(13,242,204,1) 100%)"
        status="active"
      />
    </nut-cell>
    <nut-cell>
      <nut-progress percentage="50" status="icon" />
    </nut-cell>
    <nut-cell>
      <nut-progress
        percentage="100"
        stroke-color="linear-gradient(90deg, rgba(180,236,81,1) 0%,rgba(66,147,33,1) 100%)"
        stroke-width="15"
        status="icon"
      >
        <template #icon-name>
          <Issue color="red" width="15px" height="15px"></Issue>
        </template>
      </nut-progress>
    </nut-cell>

    <h2>设置百分比</h2>
    <nut-cell>
      <nut-progress :percentage="val" />
    </nut-cell>
    <nut-cell>
      <nut-button type="default" @click="setReduceVal">减少</nut-button>
      <nut-button type="primary" @click="setAddVal">增加</nut-button>
    </nut-cell>
  </Demo>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import { Issue } from '@nutui/icons-vue-taro';
const val = ref(0);
const setAddVal = () => {
  if (val.value >= 100) {
    return false;
  }
  val.value += 10;
};
const setReduceVal = () => {
  if (val.value <= 0) {
    return false;
  }
  val.value -= 10;
};
</script>

<style>
.nut-button {
  margin-right: 10px;
}
</style>
