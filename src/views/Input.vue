<script setup lang="ts">
import { ref, watchEffect } from 'vue'
const value = ref('')
const lazyValue = ref('')
watchEffect(() => {
  console.log('value:', value.value)
})
watchEffect(() => {
  console.log('lazyValue:', lazyValue.value)
})
function onChange(e: Event) {
  console.log('change e:', e)
}
function onEnter(e: KeyboardEvent) {
  console.log('enter e:', e)
}
</script>
<template>
  <div>
    <h1>{{ $route.name }} {{ $route.meta.title }}</h1>
    <h2 class="mt30 mb10">基本使用</h2>
    <Space vertical>
      <Input v-model:value="value" placeholder="Basic usage" @change="onChange" @enter="onEnter" />
      <Input v-model:value.lazy="lazyValue" placeholder="Lazy usage" @change="onChange" />
    </Space>
    <h2 class="mt30 mb10">前缀和后缀</h2>
    <Space vertical>
      <Input v-model:value="value" placeholder="Basic usage">
        <template #prefix>
          <svg
            focusable="false"
            class="u-svg"
            data-icon="user"
            width="1em"
            height="1em"
            fill="currentColor"
            aria-hidden="true"
            viewBox="64 64 896 896"
          >
            <path
              d="M858.5 763.6a374 374 0 00-80.6-119.5 375.63 375.63 0 00-119.5-80.6c-.4-.2-.8-.3-1.2-.5C719.5 518 760 444.7 760 362c0-137-111-248-248-248S264 225 264 362c0 82.7 40.5 156 102.8 201.1-.4.2-.8.3-1.2.5-44.8 18.9-85 46-119.5 80.6a375.63 375.63 0 00-80.6 119.5A371.7 371.7 0 00136 901.8a8 8 0 008 8.2h60c4.4 0 7.9-3.5 8-7.8 2-77.2 33-149.5 87.8-204.3 56.7-56.7 132-87.9 212.2-87.9s155.5 31.2 212.2 87.9C779 752.7 810 825 812 902.2c.1 4.4 3.6 7.8 8 7.8h60a8 8 0 008-8.2c-1-47.8-10.9-94.3-29.5-138.2zM512 534c-45.9 0-89.1-17.9-121.6-50.4S340 407.9 340 362c0-45.9 17.9-89.1 50.4-121.6S466.1 190 512 190s89.1 17.9 121.6 50.4S684 316.1 684 362c0 45.9-17.9 89.1-50.4 121.6S557.9 534 512 534z"
            ></path>
          </svg>
        </template>
        <template #suffix>
          <Tooltip :max-width="150" tooltip="Extra information">
            <svg
              focusable="false"
              class="u-svg"
              data-icon="info-circle"
              width="1em"
              height="1em"
              fill="currentColor"
              aria-hidden="true"
              viewBox="64 64 896 896"
            >
              <path
                d="M512 64C264.6 64 64 264.6 64 512s200.6 448 448 448 448-200.6 448-448S759.4 64 512 64zm0 820c-205.4 0-372-166.6-372-372s166.6-372 372-372 372 166.6 372 372-166.6 372-372 372z"
              ></path>
              <path
                d="M464 336a48 48 0 1096 0 48 48 0 10-96 0zm72 112h-48c-4.4 0-8 3.6-8 8v272c0 4.4 3.6 8 8 8h48c4.4 0 8-3.6 8-8V456c0-4.4-3.6-8-8-8z"
              ></path>
            </svg>
          </Tooltip>
        </template>
      </Input>
      <Input v-model:value="value" prefix="￥" suffix="RMB" />
    </Space>
    <h2 class="mt30 mb10">三种大小</h2>
    <Space vertical>
      <Input
        size="large"
        :width="500"
        show-count
        :maxlength="20"
        allow-clear
        v-model:value="value"
        placeholder="large size"
        prefix="￥"
        suffix="RMB"
        addon-before="Http://"
        addon-after=".com"
      />
      <Input
        :width="500"
        show-count
        :maxlength="20"
        allow-clear
        v-model:value="value"
        placeholder="default size"
        prefix="￥"
        suffix="RMB"
        addon-before="Http://"
        addon-after=".com"
      />
      <Input
        size="small"
        :width="500"
        show-count
        :maxlength="20"
        allow-clear
        v-model:value="value"
        placeholder="small size"
        prefix="￥"
        suffix="RMB"
        addon-before="Http://"
        addon-after=".com"
      />
    </Space>
    <h2 class="mt30 mb10">前置/后置标签</h2>
    <Space vertical>
      <Input
        :width="300"
        show-count
        :maxlength="20"
        v-model:value="value"
        placeholder="Basic usage"
        prefix="￥"
        suffix="RMB"
        addon-before="Http://"
        addon-after=".com"
      />
      <Input v-model:value="value">
        <template #addonAfter>
          <svg
            focusable="false"
            class="u-svg"
            data-icon="setting"
            width="1em"
            height="1em"
            fill="currentColor"
            aria-hidden="true"
            viewBox="64 64 896 896"
          >
            <path
              d="M924.8 625.7l-65.5-56c3.1-19 4.7-38.4 4.7-57.8s-1.6-38.8-4.7-57.8l65.5-56a32.03 32.03 0 009.3-35.2l-.9-2.6a443.74 443.74 0 00-79.7-137.9l-1.8-2.1a32.12 32.12 0 00-35.1-9.5l-81.3 28.9c-30-24.6-63.5-44-99.7-57.6l-15.7-85a32.05 32.05 0 00-25.8-25.7l-2.7-.5c-52.1-9.4-106.9-9.4-159 0l-2.7.5a32.05 32.05 0 00-25.8 25.7l-15.8 85.4a351.86 351.86 0 00-99 57.4l-81.9-29.1a32 32 0 00-35.1 9.5l-1.8 2.1a446.02 446.02 0 00-79.7 137.9l-.9 2.6c-4.5 12.5-.8 26.5 9.3 35.2l66.3 56.6c-3.1 18.8-4.6 38-4.6 57.1 0 19.2 1.5 38.4 4.6 57.1L99 625.5a32.03 32.03 0 00-9.3 35.2l.9 2.6c18.1 50.4 44.9 96.9 79.7 137.9l1.8 2.1a32.12 32.12 0 0035.1 9.5l81.9-29.1c29.8 24.5 63.1 43.9 99 57.4l15.8 85.4a32.05 32.05 0 0025.8 25.7l2.7.5a449.4 449.4 0 00159 0l2.7-.5a32.05 32.05 0 0025.8-25.7l15.7-85a350 350 0 0099.7-57.6l81.3 28.9a32 32 0 0035.1-9.5l1.8-2.1c34.8-41.1 61.6-87.5 79.7-137.9l.9-2.6c4.5-12.3.8-26.3-9.3-35zM788.3 465.9c2.5 15.1 3.8 30.6 3.8 46.1s-1.3 31-3.8 46.1l-6.6 40.1 74.7 63.9a370.03 370.03 0 01-42.6 73.6L721 702.8l-31.4 25.8c-23.9 19.6-50.5 35-79.3 45.8l-38.1 14.3-17.9 97a377.5 377.5 0 01-85 0l-17.9-97.2-37.8-14.5c-28.5-10.8-55-26.2-78.7-45.7l-31.4-25.9-93.4 33.2c-17-22.9-31.2-47.6-42.6-73.6l75.5-64.5-6.5-40c-2.4-14.9-3.7-30.3-3.7-45.5 0-15.3 1.2-30.6 3.7-45.5l6.5-40-75.5-64.5c11.3-26.1 25.6-50.7 42.6-73.6l93.4 33.2 31.4-25.9c23.7-19.5 50.2-34.9 78.7-45.7l37.9-14.3 17.9-97.2c28.1-3.2 56.8-3.2 85 0l17.9 97 38.1 14.3c28.7 10.8 55.4 26.2 79.3 45.8l31.4 25.8 92.8-32.9c17 22.9 31.2 47.6 42.6 73.6L781.8 426l6.5 39.9zM512 326c-97.2 0-176 78.8-176 176s78.8 176 176 176 176-78.8 176-176-78.8-176-176-176zm79.2 255.2A111.6 111.6 0 01512 614c-29.9 0-58-11.7-79.2-32.8A111.6 111.6 0 01400 502c0-29.9 11.7-58 32.8-79.2C454 401.6 482.1 390 512 390c29.9 0 58 11.6 79.2 32.8A111.6 111.6 0 01624 502c0 29.9-11.7 58-32.8 79.2z"
            ></path>
          </svg>
        </template>
      </Input>
    </Space>
    <h2 class="mt30 mb10">带移除图标</h2>
    <Space>
      <Input allow-clear v-model:value="value" placeholder="input with clear icon" />
    </Space>
    <h2 class="mt30 mb10">密码框</h2>
    <Space>
      <Input password v-model:value="value" placeholder="input password" />
    </Space>
    <h2 class="mt30 mb10">带数字提示</h2>
    <Space>
      <Input show-count allow-clear v-model:value="value" :maxlength="20" placeholder="please input" />
    </Space>
    <h2 class="mt30 mb10">禁用</h2>
    <Space>
      <Input disabled v-model:value="value" />
    </Space>
  </div>
</template>
<style lang="less" scoped>
.u-svg {
  display: inline-flex;
  align-items: center;
  line-height: 0;
  text-align: center;
  vertical-align: -0.125em;
  fill: rgba(0, 0, 0, 0.88);
}
</style>
