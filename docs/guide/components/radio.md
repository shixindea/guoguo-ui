# 单选框 Radio

<BackTop />
<Watermark fullscreen content="Vue Amazing UI" />

## 何时使用

- 用于在多个备选项中选中单个状态
- 和 Select 的区别是，Radio 所有选项默认可见，方便用户在比较中选择，因此选项不宜过多

<script setup lang="ts">
import { ref, watchEffect } from 'vue'
const options = ref([
      {
        label: '北京市',
        value: 1
      },
      {
        label: '纽约市',
        value: 2
      },
      {
        label: '布宜诺斯艾利斯',
        value: 3
      },
      {
        label: '伊斯坦布尔',
        value: 4
      },
      {
        label: '拜占庭',
        value: 5
      },
      {
        label: '君士坦丁堡',
        value: 6
      }
    ])
const optionsDisabled = ref([
      {
        label: '北京市',
        value: 1
      },
      {
        label: '纽约市',
        value: 2,
        disabled: true
      },
      {
        label: '布宜诺斯艾利斯',
        value: 3
      },
      {
        label: '伊斯坦布尔',
        value: 4
      },
      {
        label: '拜占庭',
        value: 5
      },
      {
        label: '君士坦丁堡',
        value: 6
      }
    ])
const value = ref(1)
watchEffect(() => {
  console.log('value:', value.value)
})
const radioGap = ref(24)
function onChange (value: any) {
  console.log('change:', value)
}
const sizeOptions = [
  {
    label: 'large',
    value: 'large'
  },
  {
    label: 'default',
    value: 'default'
  },
  {
    label: 'small',
    value: 'small'
  }
]
const buttonSize = ref('large')
</script>

## 基本使用

<Radio :options="options" v-model:value="value" @change="onChange" />

::: details Show Code

```vue
<script setup lang="ts">
import { ref, watchEffect } from 'vue'
const options = ref([
      {
        label: '北京市',
        value: 1
      },
      {
        label: '纽约市',
        value: 2
      },
      {
        label: '布宜诺斯艾利斯',
        value: 3
      },
      {
        label: '伊斯坦布尔',
        value: 4
      },
      {
        label: '拜占庭',
        value: 5
      },
      {
        label: '君士坦丁堡',
        value: 6
      }
    ])
const value = ref(1)
watchEffect(() => {
  console.log('value:', value.value)
})
function onChange(value: any) {
  console.log('change:', value)
}
</script>
<template>
  <Radio :options="options" v-model:value="value" @change="onChange" />
</template>
```

:::

## 按钮样式

<Radio :options="options" v-model:value="value" button />

::: details Show Code

```vue
<script setup lang="ts">
import { ref } from 'vue'
const options = ref([
        {
          label: '北京市',
          value: 1
        },
        {
          label: '纽约市',
          value: 2
        },
        {
          label: '布宜诺斯艾利斯',
          value: 3
        },
        {
          label: '伊斯坦布尔',
          value: 4
        },
        {
          label: '拜占庭',
          value: 5
        },
        {
          label: '君士坦丁堡',
          value: 6
        }
      ])
const value = ref(1)
</script>
<template>
  <Radio :options="options" v-model:value="value" button />
</template>
```

:::

## 填底的按钮样式

<Radio :options="options" v-model:value="value" button button-style="solid" />

::: details Show Code

```vue
<script setup lang="ts">
import { ref } from 'vue'
const options = ref([
        {
          label: '北京市',
          value: 1
        },
        {
          label: '纽约市',
          value: 2
        },
        {
          label: '布宜诺斯艾利斯',
          value: 3
        },
        {
          label: '伊斯坦布尔',
          value: 4
        },
        {
          label: '拜占庭',
          value: 5
        },
        {
          label: '君士坦丁堡',
          value: 6
        }
      ])
const value = ref(1)
</script>
<template>
  <Radio :options="options" v-model:value="value" button button-style="solid" />
</template>
```

:::

## 禁用

<Space vertical gap="middle">
  <Radio :options="options" v-model:value="value" disabled />
  <Radio :options="options" v-model:value="value" button disabled />
</Space>

::: details Show Code

```vue
<script setup lang="ts">
import { ref } from 'vue'
const options = ref([
        {
          label: '北京市',
          value: 1
        },
        {
          label: '纽约市',
          value: 2
        },
        {
          label: '布宜诺斯艾利斯',
          value: 3
        },
        {
          label: '伊斯坦布尔',
          value: 4
        },
        {
          label: '拜占庭',
          value: 5
        },
        {
          label: '君士坦丁堡',
          value: 6
        }
      ])
const value = ref(1)
</script>
<template>
  <Space vertical gap="middle">
    <Radio :options="options" v-model:value="value" disabled />
    <Radio :options="options" v-model:value="value" button disabled />
  </Space>
</template>
```

:::

## 禁用选项

<Space vertical gap="middle">
  <Radio :options="optionsDisabled" v-model:value="value" />
  <Radio :options="optionsDisabled" v-model:value="value" button />
  <Radio :options="optionsDisabled" v-model:value="value" button button-style="solid" />
</Space>

::: details Show Code

```vue
<script setup lang="ts">
import { ref, watchEffect } from 'vue'
const optionsDisabled = ref([
      {
        label: '北京市',
        value: 1
      },
      {
        label: '纽约市',
        value: 2,
        disabled: true
      },
      {
        label: '布宜诺斯艾利斯',
        value: 3
      },
      {
        label: '伊斯坦布尔',
        value: 4
      },
      {
        label: '拜占庭',
        value: 5
      },
      {
        label: '君士坦丁堡',
        value: 6
      }
    ])

const value = ref(1)
watchEffect(() => {
  console.log('value:', value.value)
})
</script>
<template>
  <Space vertical gap="middle">
    <Radio :options="optionsDisabled" v-model:value="value" />
    <Radio :options="optionsDisabled" v-model:value="value" button />
    <Radio :options="optionsDisabled" v-model:value="value" button button-style="solid" />
  </Space>
</template>
```

:::

## 垂直排列

<Radio vertical :options="options" v-model:value="value" />

::: details Show Code

```vue
<script setup lang="ts">
import { ref, watchEffect } from 'vue'
const options = ref([
      {
        label: '北京市',
        value: 1
      },
      {
        label: '纽约市',
        value: 2
      },
      {
        label: '布宜诺斯艾利斯',
        value: 3
      },
      {
        label: '伊斯坦布尔',
        value: 4
      },
      {
        label: '拜占庭',
        value: 5
      },
      {
        label: '君士坦丁堡',
        value: 6
      }
    ])
const value = ref(1)
watchEffect(() => {
  console.log('value:', value.value)
})
</script>
<template>
  <Radio vertical :options="options" v-model:value="value" />
</template>
```

:::

## 自定义间距

<Flex vertical gap="middle">
  <Slider v-model:value="radioGap" width="50%" />
  <Radio :gap="radioGap" :options="options" v-model:value="value" />
</Flex>

::: details Show Code

```vue
<script setup lang="ts">
import { ref, watchEffect } from 'vue'
const options = ref([
      {
        label: '北京市',
        value: 1
      },
      {
        label: '纽约市',
        value: 2
      },
      {
        label: '布宜诺斯艾利斯',
        value: 3
      },
      {
        label: '伊斯坦布尔',
        value: 4
      },
      {
        label: '拜占庭',
        value: 5
      },
      {
        label: '君士坦丁堡',
        value: 6
      }
    ])
const value = ref(1)
watchEffect(() => {
  console.log('value:', value.value)
})
const radioGap = ref(24)
</script>
<template>
  <Flex vertical gap="middle">
    <Slider v-model:value="radioGap" width="50%" />
    <Radio :gap="radioGap" :options="options" v-model:value="value" />
    </Flex>
</template>
```

:::

## 按钮大小

<Space vertical gap="middle">
  <Radio :options="sizeOptions" v-model:value="buttonSize" />
  <Radio :options="options" v-model:value="value" button :button-size="buttonSize" />
  <Radio :options="options" v-model:value="value" button button-style="solid" :button-size="buttonSize" />
</Space>

::: details Show Code

```vue
<script setup lang="ts">
import { ref, watchEffect } from 'vue'
const options = ref([
      {
        label: '北京市',
        value: 1
      },
      {
        label: '纽约市',
        value: 2
      },
      {
        label: '布宜诺斯艾利斯',
        value: 3
      },
      {
        label: '伊斯坦布尔',
        value: 4
      },
      {
        label: '拜占庭',
        value: 5
      },
      {
        label: '君士坦丁堡',
        value: 6
      }
    ])
const value = ref(1)
watchEffect(() => {
  console.log('value:', value.value)
})
const sizeOptions = [
  {
    label: 'large',
    value: 'large'
  },
  {
    label: 'default',
    value: 'default'
  },
  {
    label: 'small',
    value: 'small'
  }
]
const buttonSize = ref('large')
</script>
<template>
  <Space vertical gap="middle">
    <Radio :options="sizeOptions" v-model:value="buttonSize" />
    <Radio :options="options" v-model:value="value" button :button-size="buttonSize" />
    <Radio :options="options" v-model:value="value" button button-style="solid" :button-size="buttonSize" />
  </Space>
</template>
```

:::

## APIs

### Radio

参数 | 说明 | 类型 | 默认值 | 必传
-- | -- | -- | -- | --
options | 单选元素数据 | [Option](#option-type)[] | [] | true
disabled | 是否禁用 | boolean | false | false
vertical | 是否垂直排列，仅当 `button: false` 时生效 | boolean | false | false
value <Tag color="cyan">v-model</Tag> | 当前选中的值 | any | null | false
gap | 多个单选框之间的间距，单位`px`，垂直排列时，间距即垂直间距，仅当 `button: false` 时生效 | number | 8 | false
button | 是否启用按钮样式 | boolean | false | false
buttonStyle | 按钮样式风格 | 'outline' &#124; 'solid' ｜ 'outline' | false
buttonSize | 按钮大小，仅当 `button: true` 时生效 | 'default' &#124; 'large' &#124; 'small' | false

### Option Type

名称 | 说明 | 类型 | 必传
-- | -- | -- | --
label | 选项名 | string | true
value | 选项值 | any | true
disabled | 是否禁用单个单选器 | boolean | false

## Events

事件名称 | 说明 | 参数
-- | -- | --
change | 选项变化时的回调函数 | (value: any) => void
