# 加载中 Spin

<BackTop />
<Watermark fullscreen content="Vue Amazing UI" />

<br/>

*用于页面和区块的加载中状态*

## 何时使用

- 页面局部处于等待异步数据或正在渲染过程时，合适的加载动效会有效缓解用户的焦虑

<script setup lang="ts">
import { ref } from 'vue'

const tip = ref('加载中...')
const spinning = ref(true)
</script>

## 基本使用

<Flex align="center">
  Loading state:<Switch v-model:checked="spinning" />
</Flex>

<br/>

<Spin :spinning="spinning">
  <p class="spin-content">当 spinning 为 false 时，不显示 loading 状态；当 spinning 为 true 时，显示 loading 效果；如果不设置 tip 描述文案时，则只有 loading 效果水平垂直居中；如果设置了 tip 描述文案，则 loading 效果和 tip 描述文案一起水平垂直居中。</p>
</Spin>

::: details Show Code

```vue
<script setup lang="ts">
import { ref } from 'vue'
const spinning = ref(true)
</script>
<template>
  <Spin :spinning="spinning">
    <p class="spin-content">当 spinning 为 false 时，不显示 loading 状态；当 spinning 为 true 时，显示 loading 效果；如果不设置 tip 描述文案时，则只有 loading 效果水平垂直居中；如果设置了 tip 描述文案，则 loading 效果和 tip 描述文案一起水平垂直居中。</p>
  </Spin>
</template>
<style lang="less" scoped>
.spin-content {
  display: inline-block;
  border: 1px solid #91d5ff;
  border-radius: 6px;
  background-color: #e6f7ff;
  padding: 16px;
}
</style>
```

:::

## 旋转的点

<Spin :spinning="spinning" indicator="spin-dot">
  <p class="spin-content">当 spinning 为 false 时，不显示 loading 状态；当 spinning 为 true 时，显示 loading 效果；如果不设置 tip 描述文案时，则只有 loading 效果水平垂直居中；如果设置了 tip 描述文案，则 loading 效果和 tip 描述文案一起水平垂直居中。</p>
</Spin>

::: details Show Code

```vue
<script setup lang="ts">
import { ref } from 'vue'
const spinning = ref(true)
</script>
<template>
  <Spin :spinning="spinning" indicator="spin-dot">
    <p class="spin-content">当 spinning 为 false 时，不显示 loading 状态；当 spinning 为 true 时，显示 loading 效果；如果不设置 tip 描述文案时，则只有 loading 效果水平垂直居中；如果设置了 tip 描述文案，则 loading 效果和 tip 描述文案一起水平垂直居中。</p>
  </Spin>
</template>
<style lang="less" scoped>
.spin-content {
  display: inline-block;
  border: 1px solid #91d5ff;
  border-radius: 6px;
  background-color: #e6f7ff;
  padding: 16px;
}
</style>
```

:::

## 旋转的线

<Spin :spinning="spinning" indicator="spin-line">
  <p class="spin-content">当 spinning 为 false 时，不显示 loading 状态；当 spinning 为 true 时，显示 loading 效果；如果不设置 tip 描述文案时，则只有 loading 效果水平垂直居中；如果设置了 tip 描述文案，则 loading 效果和 tip 描述文案一起水平垂直居中。</p>
</Spin>

::: details Show Code

```vue
<script setup lang="ts">
import { ref } from 'vue'
const spinning = ref(true)
</script>
<template>
  <Spin :spinning="spinning" indicator="spin-line">
    <p class="spin-content">当 spinning 为 false 时，不显示 loading 状态；当 spinning 为 true 时，显示 loading 效果；如果不设置 tip 描述文案时，则只有 loading 效果水平垂直居中；如果设置了 tip 描述文案，则 loading 效果和 tip 描述文案一起水平垂直居中。</p>
  </Spin>
</template>
<style lang="less" scoped>
.spin-content {
  display: inline-block;
  border: 1px solid #91d5ff;
  border-radius: 6px;
  background-color: #e6f7ff;
  padding: 16px;
}
</style>
```

:::

## 四分之一圆形指示符

<Spin :spinning="spinning" indicator="quarter-circle">
  <p class="spin-content">当 spinning 为 false 时，不显示 loading 状态；当 spinning 为 true 时，显示 loading 效果；如果不设置 tip 描述文案时，则只有 loading 效果水平垂直居中；如果设置了 tip 描述文案，则 loading 效果和 tip 描述文案一起水平垂直居中。</p>
</Spin>

::: details Show Code

```vue
<script setup lang="ts">
import { ref } from 'vue'
const spinning = ref(true)
</script>
<template>
  <Spin :spinning="spinning" indicator="quarter-circle">
    <p class="spin-content">当 spinning 为 false 时，不显示 loading 状态；当 spinning 为 true 时，显示 loading 效果；如果不设置 tip 描述文案时，则只有 loading 效果水平垂直居中；如果设置了 tip 描述文案，则 loading 效果和 tip 描述文案一起水平垂直居中。</p>
  </Spin>
</template>
<style lang="less" scoped>
.spin-content {
  display: inline-block;
  border: 1px solid #91d5ff;
  border-radius: 6px;
  background-color: #e6f7ff;
  padding: 16px;
}
</style>
```

:::

## 二分之一圆形指示符

<Spin :spinning="spinning" indicator="half-circle">
  <p class="spin-content">当 spinning 为 false 时，不显示 loading 状态；当 spinning 为 true 时，显示 loading 效果；如果不设置 tip 描述文案时，则只有 loading 效果水平垂直居中；如果设置了 tip 描述文案，则 loading 效果和 tip 描述文案一起水平垂直居中。</p>
</Spin>

::: details Show Code

```vue
<script setup lang="ts">
import { ref } from 'vue'
const spinning = ref(true)
</script>
<template>
  <Spin :spinning="spinning" indicator="half-circle">
    <p class="spin-content">当 spinning 为 false 时，不显示 loading 状态；当 spinning 为 true 时，显示 loading 效果；如果不设置 tip 描述文案时，则只有 loading 效果水平垂直居中；如果设置了 tip 描述文案，则 loading 效果和 tip 描述文案一起水平垂直居中。</p>
  </Spin>
</template>
<style lang="less" scoped>
.spin-content {
  display: inline-block;
  border: 1px solid #91d5ff;
  border-radius: 6px;
  background-color: #e6f7ff;
  padding: 16px;
}
</style>
```

:::

## 四分之三圆形指示符

<Spin :spinning="spinning" indicator="three-quarters-circle">
  <p class="spin-content">当 spinning 为 false 时，不显示 loading 状态；当 spinning 为 true 时，显示 loading 效果；如果不设置 tip 描述文案时，则只有 loading 效果水平垂直居中；如果设置了 tip 描述文案，则 loading 效果和 tip 描述文案一起水平垂直居中。</p>
</Spin>

::: details Show Code

```vue
<script setup lang="ts">
import { ref } from 'vue'
const spinning = ref(true)
</script>
<template>
  <Spin :spinning="spinning" indicator="three-quarters-circle">
    <p class="spin-content">当 spinning 为 false 时，不显示 loading 状态；当 spinning 为 true 时，显示 loading 效果；如果不设置 tip 描述文案时，则只有 loading 效果水平垂直居中；如果设置了 tip 描述文案，则 loading 效果和 tip 描述文案一起水平垂直居中。</p>
  </Spin>
</template>
<style lang="less" scoped>
.spin-content {
  display: inline-block;
  border: 1px solid #91d5ff;
  border-radius: 6px;
  background-color: #e6f7ff;
  padding: 16px;
}
</style>
```

:::

## 动态圆形指示符

<Spin :spinning="spinning" indicator="dynamic-circle">
  <p class="spin-content">当 spinning 为 false 时，不显示 loading 状态；当 spinning 为 true 时，显示 loading 效果；如果不设置 tip 描述文案时，则只有 loading 效果水平垂直居中；如果设置了 tip 描述文案，则 loading 效果和 tip 描述文案一起水平垂直居中。</p>
</Spin>

::: details Show Code

```vue
<script setup lang="ts">
import { ref } from 'vue'
const spinning = ref(true)
</script>
<template>
  <Spin :spinning="spinning" indicator="dynamic-circle">
    <p class="spin-content">当 spinning 为 false 时，不显示 loading 状态；当 spinning 为 true 时，显示 loading 效果；如果不设置 tip 描述文案时，则只有 loading 效果水平垂直居中；如果设置了 tip 描述文案，则 loading 效果和 tip 描述文案一起水平垂直居中。</p>
  </Spin>
</template>
<style lang="less" scoped>
.spin-content {
  display: inline-block;
  border: 1px solid #91d5ff;
  border-radius: 6px;
  background-color: #e6f7ff;
  padding: 16px;
}
</style>
```

:::

## 魔法圆环指示符

<Spin :spinning="spinning" indicator="magic-ring">
  <p class="spin-content">当 spinning 为 false 时，不显示 loading 状态；当 spinning 为 true 时，显示 loading 效果；如果不设置 tip 描述文案时，则只有 loading 效果水平垂直居中；如果设置了 tip 描述文案，则 loading 效果和 tip 描述文案一起水平垂直居中。</p>
</Spin>

::: details Show Code

```vue
<script setup lang="ts">
import { ref } from 'vue'
const spinning = ref(true)
</script>
<template>
  <Spin :spinning="spinning" indicator="magic-ring">
    <p class="spin-content">当 spinning 为 false 时，不显示 loading 状态；当 spinning 为 true 时，显示 loading 效果；如果不设置 tip 描述文案时，则只有 loading 效果水平垂直居中；如果设置了 tip 描述文案，则 loading 效果和 tip 描述文案一起水平垂直居中。</p>
  </Spin>
</template>
<style lang="less" scoped>
.spin-content {
  display: inline-block;
  border: 1px solid #91d5ff;
  border-radius: 6px;
  background-color: #e6f7ff;
  padding: 16px;
}
</style>
```

:::

## 自定义描述文案

<Space>
  <Spin class="u-spin" tip="加载中..." :spinning="spinning" />
  <Spin class="u-spin" tip="加载中..." :spinning="spinning" indicator="spin-dot" />
  <Spin class="u-spin" tip="加载中..." :spinning="spinning" indicator="spin-line" />
  <Spin class="u-spin" tip="加载中..." :spinning="spinning" indicator="quarter-circle" />
  <Spin class="u-spin" tip="加载中..." :spinning="spinning" indicator="half-circle" />
  <Spin class="u-spin" tip="加载中..." :spinning="spinning" indicator="three-quarters-circle" />
  <Spin class="u-spin" tip="加载中..." :spinning="spinning" indicator="dynamic-circle" />
  <Spin class="u-spin" tip="加载中..." :spinning="spinning" indicator="magic-ring" />
</Space>

::: details Show Code

```vue
<script setup lang="ts">
import { ref } from 'vue'
const spinning = ref(true)
</script>
<template>
  <Space>
    <Spin class="u-spin" tip="加载中..." :spinning="spinning" />
    <Spin class="u-spin" tip="加载中..." :spinning="spinning" indicator="spin-dot" />
    <Spin class="u-spin" tip="加载中..." :spinning="spinning" indicator="spin-line" />
    <Spin class="u-spin" tip="加载中..." :spinning="spinning" indicator="quarter-circle" />
    <Spin class="u-spin" tip="加载中..." :spinning="spinning" indicator="half-circle" />
    <Spin class="u-spin" tip="加载中..." :spinning="spinning" indicator="three-quarters-circle" />
    <Spin class="u-spin" tip="加载中..." :spinning="spinning" indicator="dynamic-circle" />
    <Spin class="u-spin" tip="加载中..." :spinning="spinning" indicator="magic-ring" />
  </Space>
</template>
<style lang="less" scoped>
.u-spin {
  width: 100px !important;
  height: 100px !important;
}
</style>
```

:::

## 自定义颜色

<Space>
  <Spin class="u-spin" color="#fadb14" :spinning="spinning" />
  <Spin class="u-spin" color="#fadb14" :spinning="spinning" indicator="spin-dot" />
  <Spin class="u-spin" color="#fadb14" :spinning="spinning" indicator="spin-line" />
  <Spin class="u-spin" color="#fadb14" :spinning="spinning" indicator="quarter-circle" />
  <Spin class="u-spin" color="#fadb14" :spinning="spinning" indicator="half-circle" />
  <Spin class="u-spin" color="#fadb14" :spinning="spinning" indicator="three-quarters-circle" />
  <Spin class="u-spin" color="#fadb14" :spinning="spinning" indicator="dynamic-circle" />
  <Spin class="u-spin" color="#fadb14" ring-color="#ffe58f" :spinning="spinning" indicator="magic-ring" />
</Space>

::: details Show Code

```vue
<script setup lang="ts">
import { ref } from 'vue'
const spinning = ref(true)
</script>
<template>
  <Space>
    <Spin class="u-spin" color="#fadb14" :spinning="spinning" />
    <Spin class="u-spin" color="#fadb14" :spinning="spinning" indicator="spin-dot" />
    <Spin class="u-spin" color="#fadb14" :spinning="spinning" indicator="spin-line" />
    <Spin class="u-spin" color="#fadb14" :spinning="spinning" indicator="quarter-circle" />
    <Spin class="u-spin" color="#fadb14" :spinning="spinning" indicator="half-circle" />
    <Spin class="u-spin" color="#fadb14" :spinning="spinning" indicator="three-quarters-circle" />
    <Spin class="u-spin" color="#fadb14" :spinning="spinning" indicator="dynamic-circle" />
    <Spin class="u-spin" color="#fadb14" ring-color="#ffe58f" :spinning="spinning" indicator="magic-ring" />
  </Space>
</template>
<style lang="less" scoped>
.u-spin {
  width: 100px !important;
  height: 100px !important;
}
</style>
```

:::

## 各种大小

<Space vertical>
  <Space>
    <Spin class="u-spin" :spinning="spinning" size="small" />
    <Spin class="u-spin" :spinning="spinning" size="default" />
    <Spin class="u-spin" :spinning="spinning" size="large" />
  </Space>
  <Space>
    <Spin class="u-spin" :spinning="spinning" size="small" indicator="spin-dot" />
    <Spin class="u-spin" :spinning="spinning" size="default" indicator="spin-dot" />
    <Spin class="u-spin" :spinning="spinning" size="large" indicator="spin-dot" />
  </Space>
  <Space>
    <Spin class="u-spin" :spinning="spinning" size="small" indicator="spin-line" />
    <Spin class="u-spin" :spinning="spinning" size="default" indicator="spin-line" />
    <Spin class="u-spin" :spinning="spinning" size="large" indicator="spin-line" />
  </Space>
  <Space>
    <Spin class="u-spin" :spinning="spinning" size="small" indicator="quarter-circle" />
    <Spin class="u-spin" :spinning="spinning" size="default" indicator="quarter-circle" />
    <Spin class="u-spin" :spinning="spinning" size="large" indicator="quarter-circle" />
  </Space>
  <Space>
    <Spin class="u-spin" :spinning="spinning" size="small" indicator="half-circle" />
    <Spin class="u-spin" :spinning="spinning" size="default" indicator="half-circle" />
    <Spin class="u-spin" :spinning="spinning" size="large" indicator="half-circle" />
  </Space>
  <Space>
    <Spin class="u-spin" :spinning="spinning" size="small" indicator="three-quarters-circle" />
    <Spin class="u-spin" :spinning="spinning" size="default"  indicator="three-quarters-circle" />
    <Spin class="u-spin" :spinning="spinning" size="large" indicator="three-quarters-circle" />
  </Space>
  <Space>
    <Spin class="u-spin" :spinning="spinning" size="small" indicator="dynamic-circle" />
    <Spin class="u-spin" :spinning="spinning" size="default" indicator="dynamic-circle" />
    <Spin class="u-spin" :spinning="spinning" size="large" indicator="dynamic-circle" />
  </Space>
  <Space>
    <Spin class="u-spin" :spinning="spinning" size="small" indicator="magic-ring" />
    <Spin class="u-spin" :spinning="spinning" size="default" indicator="magic-ring" />
    <Spin class="u-spin" :spinning="spinning" size="large" indicator="magic-ring" />
  </Space>
</Space>

::: details Show Code

```vue
<script setup lang="ts">
import { ref } from 'vue'
const spinning = ref(true)
</script>
<template>
  <Space vertical>
    <Space>
      <Spin class="u-spin" :spinning="spinning" size="small" />
      <Spin class="u-spin" :spinning="spinning" size="default" />
      <Spin class="u-spin" :spinning="spinning" size="large" />
    </Space>
    <Space>
      <Spin class="u-spin" :spinning="spinning" size="small" indicator="spin-dot" />
      <Spin class="u-spin" :spinning="spinning" size="default" indicator="spin-dot" />
      <Spin class="u-spin" :spinning="spinning" size="large" indicator="spin-dot" />
    </Space>
    <Space>
      <Spin class="u-spin" :spinning="spinning" size="small" indicator="spin-line" />
      <Spin class="u-spin" :spinning="spinning" size="default" indicator="spin-line" />
      <Spin class="u-spin" :spinning="spinning" size="large" indicator="spin-line" />
    </Space>
    <Space>
      <Spin class="u-spin" :spinning="spinning" size="small" indicator="quarter-circle" />
      <Spin class="u-spin" :spinning="spinning" size="default" indicator="quarter-circle" />
      <Spin class="u-spin" :spinning="spinning" size="large" indicator="quarter-circle" />
    </Space>
    <Space>
      <Spin class="u-spin" :spinning="spinning" size="small" indicator="half-circle" />
      <Spin class="u-spin" :spinning="spinning" size="default" indicator="half-circle" />
      <Spin class="u-spin" :spinning="spinning" size="large" indicator="half-circle" />
    </Space>
    <Space>
      <Spin class="u-spin" :spinning="spinning" size="small" indicator="three-quarters-circle" />
      <Spin class="u-spin" :spinning="spinning" size="default" indicator="three-quarters-circle" />
      <Spin class="u-spin" :spinning="spinning" size="large" indicator="three-quarters-circle" />
    </Space>
    <Space>
      <Spin class="u-spin" :spinning="spinning" size="small" indicator="dynamic-circle" />
      <Spin class="u-spin" :spinning="spinning" size="default" indicator="dynamic-circle" />
      <Spin class="u-spin" :spinning="spinning" size="large" indicator="dynamic-circle" />
    </Space>
    <Space>
      <Spin class="u-spin" :spinning="spinning" size="small" indicator="magic-ring" />
      <Spin class="u-spin" :spinning="spinning" size="default" indicator="magic-ring" />
      <Spin class="u-spin" :spinning="spinning" size="large" indicator="magic-ring" />
    </Space>
  </Space>
</template>
<style lang="less" scoped>
.u-spin {
  width: 100px !important;
  height: 100px !important;
}
</style>
```

:::

<style lang="less" scoped>
.m-flex {
  display: flex;
  gap: 12px;
  align-items: center;
}
.u-h3 {
  margin-top: 0 !important;
}
.spin-content {
  display: inline-block;
  border-radius: 6px;
  border: 1px solid #91d5ff;
  background-color: #e6f7ff;
  padding: 16px;
}
.u-spin {
  width: 100px;
  height: 100px;
}
</style>

## APIs

### Spin

参数 | 说明 | 类型 | 默认值 | 必传
-- | -- | -- | -- | --
spinning | 是否为加载中状态 | boolean | true | false
size | 组件大小 | 'small' &#124; 'default' &#124; 'large' | 'default' | false
tip | 描述文案 | string | undefined | false
indicator | 加载指示符 | 'dot' &#124; 'spin-dot' &#124; 'spin-line' &#124; 'quarter-circle' &#124; 'half-circle' &#124; 'three-quarters-circle' &#124; 'dynamic-circle' &#124; 'magic-ring' | 'dot' | false
color | 主题颜色 | string | '#1677FF' | false
ringColor | 内环颜色，仅当 `indicator: 'magic-ring'` 时生效 | string | '#4096FF' | false
rotate | `spin-dot` 或 `spin-line` 初始是否旋转，仅当 `indicator: spin-dot \| spin-line` 时生效 | boolean | false | false
speed | `spin-dot` 或 `spin-line` 渐变旋转的动画速度，单位`ms`，仅当 `indicator: spin-dot \| spin-line` 时生效 | number | 600 | false
