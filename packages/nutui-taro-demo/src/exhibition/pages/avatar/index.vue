<template>
  <Demo class="full avatar-demo">
    <h2>支持三种尺寸：small、normal、large</h2>
    <nut-cell>
      <nut-avatar size="large">
        <img
          src="https://img12.360buyimg.com/imagetools/jfs/t1/196430/38/8105/14329/60c806a4Ed506298a/e6de9fb7b8490f38.png"
        />
      </nut-avatar>
      <nut-avatar size="normal">
        <img
          src="https://img12.360buyimg.com/imagetools/jfs/t1/196430/38/8105/14329/60c806a4Ed506298a/e6de9fb7b8490f38.png"
        />
      </nut-avatar>
      <nut-avatar size="small">
        <img
          src="https://img12.360buyimg.com/imagetools/jfs/t1/196430/38/8105/14329/60c806a4Ed506298a/e6de9fb7b8490f38.png"
        />
      </nut-avatar>
    </nut-cell>
    <h2>支持两种形状：square、round</h2>
    <nut-cell>
      <nut-avatar shape="square"><My /></nut-avatar>
      <nut-avatar shape="round"><My /></nut-avatar>
    </nut-cell>
    <h2>支持三种类型：图片、Icon 以及字符</h2>
    <nut-cell>
      <nut-avatar>
        <img
          src="https://img12.360buyimg.com/imagetools/jfs/t1/196430/38/8105/14329/60c806a4Ed506298a/e6de9fb7b8490f38.png"
        />
      </nut-avatar>
      <nut-avatar><My /></nut-avatar>
      <nut-avatar>王</nut-avatar>
    </nut-cell>
    <h2>Icon 和字符型可以自定义颜色及背景色</h2>
    <nut-cell>
      <nut-avatar class="demo-avatar" bg-color="#FA2C19"><My color="#fff" /></nut-avatar>
      <nut-avatar color="rgb(245, 106, 0)" bg-color="rgb(253, 227, 207)">小明</nut-avatar>
    </nut-cell>
    <h2>带徽标的头像</h2>
    <nut-cell>
      <nut-badge value="8">
        <nut-avatar shape="square"><My /></nut-avatar>
      </nut-badge>
      <nut-badge dot>
        <nut-avatar shape="square"><My /></nut-avatar>
      </nut-badge>
    </nut-cell>
    <h2>头像组合展现</h2>
    <nut-cell>
      <nut-avatar-group span="-4">
        <nut-avatar>
          <img
            src="https://img12.360buyimg.com/imagetools/jfs/t1/196430/38/8105/14329/60c806a4Ed506298a/e6de9fb7b8490f38.png"
          />
        </nut-avatar>
        <nut-avatar><My /></nut-avatar>
        <nut-avatar color="rgb(245, 106, 0)" bg-color="rgb(253, 227, 207)">小明</nut-avatar>
      </nut-avatar-group>
    </nut-cell>

    <nut-cell>
      <nut-avatar-group max-count="3" max-color="#fff" max-bg-color="#498ff2">
        <nut-avatar>
          <img
            src="https://img12.360buyimg.com/imagetools/jfs/t1/196430/38/8105/14329/60c806a4Ed506298a/e6de9fb7b8490f38.png"
          />
        </nut-avatar>
        <nut-avatar><My /></nut-avatar>
        <nut-avatar color="rgb(245, 106, 0)" bg-color="rgb(253, 227, 207)">小明</nut-avatar>
        <nut-avatar><My /></nut-avatar>
      </nut-avatar-group>
    </nut-cell>
    <h2>组合头像可控制层级方向</h2>
    <nut-cell>
      <nut-avatar-group max-count="3" z-index="right" max-content="...">
        <nut-avatar>
          <img
            src="https://img12.360buyimg.com/imagetools/jfs/t1/196430/38/8105/14329/60c806a4Ed506298a/e6de9fb7b8490f38.png"
          />
        </nut-avatar>
        <nut-avatar><My /></nut-avatar>
        <nut-avatar color="rgb(245, 106, 0)" bg-color="rgb(253, 227, 207)">小明</nut-avatar>
        <nut-avatar><My /></nut-avatar>
      </nut-avatar-group>
    </nut-cell>

    <h2>点击头像触发事件</h2>
    <nut-cell>
      <nut-avatar @click="handleClick"><My /></nut-avatar>
    </nut-cell>

    <h2 class="demo-avatar-group-title">动态添加头像<nut-button size="mini" @click="addAvatar">添加</nut-button></h2>
    <nut-cell>
      <nut-avatar-group max-count="4" z-index="right">
        <nut-avatar v-for="i in avatarCount" :key="i">
          <My v-if="i % 2 == 0" />
          <img
            v-else
            src="https://img12.360buyimg.com/imagetools/jfs/t1/196430/38/8105/14329/60c806a4Ed506298a/e6de9fb7b8490f38.png"
          />
        </nut-avatar>
      </nut-avatar-group>
    </nut-cell>
  </Demo>
</template>
<script setup lang="ts">
import { My } from '@nutui/icons-vue-taro';
import { ref } from 'vue';
const handleClick = () => {
  console.log('触发点击头像');
};

const avatarCount = ref(4);
const addAvatar = () => {
  avatarCount.value += 1;
};
</script>
<style lang="scss">
.avatar-demo {
  .nut-cell {
    align-items: flex-end;
    border-radius: 0;
    & > view {
      margin-right: 30px;
    }
  }
  .demo-avatar {
    color: #fff;
  }
  .demo-avatar-group-title {
    display: flex;
    align-items: center;
    row-gap: 8px;
    column-gap: 8px;
  }
}
</style>
