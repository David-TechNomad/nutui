<template>
  <Demo>
    <h2>基础用法</h2>
    <nut-cell>
      <nut-input-number v-model="state.val1" />
    </nut-cell>
    <h2>步长设置</h2>
    <nut-cell>
      <nut-input-number v-model="state.val2" step="5" />
    </nut-cell>
    <h2>限制输入范围</h2>
    <nut-cell>
      <nut-input-number v-model="state.val3" min="10" max="20" @overlimit="overlimit" />
    </nut-cell>
    <h2>禁用操作</h2>
    <nut-cell>
      <nut-input-number v-model="state.val4" disabled />
    </nut-cell>
    <h2>只读禁用输入框</h2>
    <nut-cell>
      <nut-input-number v-model="state.val5" readonly />
    </nut-cell>
    <h2>支持小数</h2>
    <nut-cell>
      <nut-input-number v-model="state.val6" step="0.1" decimal-places="1" readonly />
    </nut-cell>
    <h2>支持异步修改</h2>
    <nut-cell>
      <nut-input-number :model-value="state.val8" @change="onChange" />
    </nut-cell>
    <h2>自定义按钮大小</h2>
    <nut-cell>
      <nut-input-number v-model="state.val7" button-size="30" input-width="50" />
    </nut-cell>
  </Demo>
</template>

<script setup lang="ts">
import { reactive } from 'vue';
const state = reactive({
  val1: 1,
  val2: 0,
  val3: 10,
  val4: 0,
  val5: 1,
  val6: 5.5,
  val7: 1,
  val8: 1,
  step: 1.1
});
const onChange = (value: number) => {
  console.log('异步演示 2 秒后更改');
  setTimeout(() => {
    state.val8 = value;
  }, 2000);
};

const overlimit = () => {
  console.log('超出限制事件触发');
};
</script>
