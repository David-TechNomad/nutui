# Skeleton screen

### Intro

Filling gray bitmap in the area to be loaded on the page is essentially the transition effect in the process of interface loading.

### Install

```js
import { createApp } from 'vue';
import { Skeleton } from '@nutui/nutui';

const app = createApp();
app.use(Skeleton);
```

### Basic usage

:::demo

```vue
<template>
  <nut-skeleton width="250px" height="15px" animated> </nut-skeleton>
</template>
```

:::

### Incoming multiline

:::demo

```vue
<template>
  <nut-skeleton width="250px" height="15px" title animated row="3"> </nut-skeleton>
</template>
```

:::

### Show Faces

:::demo

```vue
<template>
  <nut-skeleton width="250px" height="15px" title animated avatar avatarSize="60px" row="3"> </nut-skeleton>
</template>
```

:::

### Title paragraph fillet style

:::demo

```vue
<template>
  <nut-skeleton width="250px" height="15px" animated round></nut-skeleton>
</template>
```

:::

### Picture combination

:::demo

```vue
<template>
  <div class="pic-compose">
    <nut-skeleton width="250px" height="15px" title animated row="3" class="item"> </nut-skeleton>
    <nut-skeleton width="250px" height="15px" title animated row="3" class="item"> </nut-skeleton>
  </div>
</template>
<style>
.pic-compose {
  display: flex;
  justify-content: space-between;
}
.item {
  width: 47%;
}
</style>
```

:::

### Display subcomponents

:::demo

```vue
<template>
  <div class="content">
    <nut-switch v-model="checked" />
    <nut-skeleton width="250px" height="15px" title animated avatar row="3" :loading="!checked">
      <div class="container">
        <nut-avatar size="50">
          <img
            src="https://img14.360buyimg.com/imagetools/jfs/t1/167902/2/8762/791358/603742d7E9b4275e3/e09d8f9a8bf4c0ef.png"
          />
        </nut-avatar>
      <div class="right-content">
        <div class="title">NutUI</div>
        <div class="desc"
            >A set of JD style lightweight mobile terminal Vue group library provides rich basic components and business components to help developers quickly build mobile applications.
        </div>
      </div>
    </nut-skeleton>
  </div>
</template>

<script setup>
import { ref } from 'vue';
const checked = ref(false);
</script>

<style>
  .nut-switch {
    display: flex;
    margin: 0 16px 8px 0;
  }
  .container {
    display: flex;
  }
  .right-content {
    margin-left: 19px;
    font-family: PingFangSC;
    display: flex;
    flex-direction: column;
  }
  .title {
    font-size: 14px;
    color: rgba(51, 51, 51, 1);
  }
  .desc {
    margin-top: 10px;
    font-size: 13px;
    color: rgba(154, 155, 157, 1);
  }
</style>

```

:::

## API

### Props

| Attribute | Description | Type | Default |
| --- | --- | --- | --- |
| loading | Whether to display skeleton screen | boolean | `true` |
| width | Width per row | string | `default` |
| height | Height of each row | string | `15px` |
| animated | Whether to turn on skeleton screen animation | boolean | `false` |
| avatar | Show avatar | boolean | `false` |
| avatar-shape | Avatar shape: square / round | string | `round` |
| avatar-size | Avatar size | string | `50px` |
| round | Is the title / paragraph rounded | boolean | `false` |
| title | Show paragraph titles (first line displayed) | boolean | `true` |
| row | Set the number of paragraph lines (shown below the title) | string | `1` |

### Slots

| Name | Description |
| --- | --- |
| default | Skeleton screen display content |

## Theming

### CSS Variables

The component provides the following CSS variables, which can be used to customize styles. Please refer to [ConfigProvider component](#/en-US/component/configprovider).

| Name | Default Value |
| --- | --- |
| --nut-skeleton-content-avatar-background-color | _#efefef_ |
| --nut-skeleton-content-line-background-color | _#efefef_ |
| --nut-skeleton-animation-background-color | _linear-gradient(90deg,hsla(0, 0%, 100%, 0),hsla(0, 0%, 100%, 0.5) 50%, hsla(0, 0%, 100%, 0) 80%)_ |
