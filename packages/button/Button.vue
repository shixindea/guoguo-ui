<script setup lang="ts">
import { ref, nextTick } from 'vue'
import type { Slot } from 'vue'
interface Props {
  name?: string | Slot // 按钮文本 string | slot
  type?: 'default' | 'reverse' | 'primary' | 'danger' | 'dashed' | 'text' | 'link' // 按钮类型
  size?: 'small' | 'middle' | 'large' // 按钮尺寸
  href?: string // 点击跳转的地址，与 a 链接的 href 属性一致
  target?: '_self' | '_blank' // 相当于 a 链接的 target 属性，href 存在时生效
  disabled?: boolean // 是否禁用
  loading?: boolean // 是否加载中
  center?: boolean // 是否将按钮宽度调整为其父宽度并居中展示
}
withDefaults(defineProps<Props>(), {
  name: '按钮',
  type: 'default',
  size: 'middle',
  href: '',
  target: '_self',
  disabled: false,
  loading: false,
  center: false
})
const rippleColor = {
  default: '#1677ff',
  reverse: '#1677ff',
  primary: '#1677ff',
  danger: '#ff4d4f',
  dashed: '#1677ff',
  text: 'transparent',
  link: 'transparent'
}
const wave = ref(false)
const emit = defineEmits(['click'])
function onClick(e: Event) {
  emit('click', e)
  if (wave.value) {
    wave.value = false
    nextTick(() => {
      wave.value = true
    })
  } else {
    wave.value = true
  }
}
function onKeyboard(e: KeyboardEvent) {
  onClick(e)
}
function onWaveEnd() {
  wave.value = false
}
</script>
<template>
  <div
    tabindex="0"
    :class="['m-btn-wrap', { 'btn-center': center }]"
    :style="`--ripple-color: ${rippleColor[type]}`"
    @keydown.enter.prevent="onKeyboard"
  >
    <a
      class="m-btn"
      :class="[`btn-${type} btn-${size}`, { 'btn-disabled': disabled, 'btn-loading': !href && loading }]"
      :disabled="disabled"
      :href="href ? href : 'javascript:;'"
      :target="href ? target : '_self'"
      @click="onClick"
    >
      <span v-show="!href" :class="[`m-loading-icon`, { [`loading-${size}`]: loading }]">
        <span class="u-spin-circle" :class="`spin-${size}`"></span>
      </span>
      <span class="u-text">
        <slot>{{ name }}</slot>
      </span>
      <div
        v-if="!disabled"
        class="m-button-wave"
        :class="{ 'button-wave-active': wave }"
        @animationend="onWaveEnd"
      ></div>
    </a>
  </div>
</template>
<style lang="less" scoped>
@primary: #1677ff;
@danger: #ff4d4f;
.m-btn-wrap {
  display: inline-block;
  outline: none;
  .m-btn {
    position: relative;
    display: inline-flex;
    align-items: center;
    font-weight: 400;
    line-height: 1.5714285714285714;
    color: rgba(0, 0, 0, 0.88);
    white-space: nowrap;
    text-align: center;
    background-color: transparent;
    border: 1px solid transparent;
    user-select: none;
    text-decoration: none;
    cursor: pointer;
    transition: all 0.2s cubic-bezier(0.645, 0.045, 0.355, 1);
    .m-loading-icon {
      display: inline-flex;
      align-items: center;
      text-align: left;
      opacity: 0;
      width: 0;
      height: 100%;
      transition:
        width 0.3s cubic-bezier(0.645, 0.045, 0.355, 1),
        opacity 0.3s cubic-bezier(0.645, 0.045, 0.355, 1);
      .u-spin-circle {
        border-radius: 50%;
        border-width: 1px;
        border-style: solid;
        border-color: transparent;
        border-top-color: inherit; // 显示1/4圆
        animation: loadingCircle 1s infinite linear;
        -webkit-animation: loadingCircle 1s infinite linear;
      }
      .spin-small,
      .spin-middle {
        width: 14px;
        height: 14px;
      }
      .spin-large {
        width: 16px;
        height: 16px;
      }
      @keyframes loadingCircle {
        100% {
          transform: rotate(360deg);
        }
      }
    }
    .loading-small,
    .loading-middle {
      width: 22px;
      opacity: 1;
    }
    .loading-large {
      width: 24px;
      opacity: 1;
    }
    .u-text {
      display: inline-flex;
      align-items: center;
      height: 100%;
    }
    .m-button-wave {
      position: absolute;
      pointer-events: none;
      top: 0;
      right: 0;
      bottom: 0;
      left: 0;
      animation-iteration-count: 1;
      animation-duration: 0.6s;
      animation-timing-function: cubic-bezier(0, 0, 0.2, 1), cubic-bezier(0, 0, 0.2, 1);
      border-radius: inherit;
    }
    .button-wave-active {
      z-index: 1;
      animation-name: button-wave-spread, button-wave-opacity;
      @keyframes button-wave-spread {
        from {
          box-shadow: 0 0 0.5px 0 var(--ripple-color);
        }
        to {
          box-shadow: 0 0 0.5px 4.5px var(--ripple-color);
        }
      }
      @keyframes button-wave-opacity {
        from {
          opacity: 0.6;
        }
        to {
          opacity: 0;
        }
      }
    }
  }
  .btn-loading {
    opacity: 0.65;
    pointer-events: none;
  }
  .btn-default {
    background-color: #ffffff;
    border-color: #d9d9d9;
    box-shadow: 0 2px 0 rgba(0, 0, 0, 0.02);
    &:hover {
      color: fade(@primary, 80%);
      border-color: fade(@primary, 80%);
    }
    &:active {
      color: shade(@primary, 12%);
      border-color: shade(@primary, 12%);
    }
  }
  .btn-reverse {
    .btn-default();
    &:hover {
      color: #fff;
      background-color: fade(@primary, 80%);
      border-color: fade(@primary, 80%);
    }
    &:active {
      color: #fff;
      background-color: shade(@primary, 12%);
      border-color: shade(@primary, 12%);
    }
  }
  .btn-primary {
    color: #fff;
    background-color: @primary;
    box-shadow: 0 2px 0 rgba(5, 145, 255, 0.1);
    &:hover {
      background-color: fade(@primary, 80%);
      border-color: fade(@primary, 80%);
    }
    &:active {
      background-color: shade(@primary, 12%);
      border-color: shade(@primary, 12%);
    }
  }
  .btn-danger {
    color: #fff;
    background-color: @danger;
    border-color: @danger;
    box-shadow: 0 2px 0 rgb(0 0 0 / 5%);
    &:hover {
      background-color: fade(@danger, 80%);
      border-color: fade(@danger, 80%);
    }
    &:active {
      background-color: shade(@danger, 12%);
      border-color: shade(@danger, 12%);
    }
  }
  .btn-dashed {
    .btn-default();
    border-style: dashed;
  }
  .btn-text {
    &:hover {
      background-color: rgba(0, 0, 0, 0.06);
    }
    &:active {
      background-color: rgba(0, 0, 0, 0.15);
    }
  }
  .btn-link {
    color: @primary;
    &:hover {
      color: fade(@primary, 80%);
    }
    &:active {
      color: shade(@primary, 12%);
    }
  }
  .btn-small {
    font-size: 14px;
    height: 24px;
    padding: 0px 7px;
    border-radius: 4px;
  }
  .btn-middle {
    font-size: 14px;
    height: 32px;
    padding: 4px 15px;
    border-radius: 6px;
  }
  .btn-large {
    font-size: 16px;
    height: 40px;
    padding: 6.428571428571429px 15px;
    border-radius: 8px;
  }
  .btn-disabled {
    border-color: #d9d9d9;
    color: rgba(0, 0, 0, 0.25);
    background-color: rgba(0, 0, 0, 0.04);
    box-shadow: none;
    cursor: not-allowed;
    &:hover,
    &:active {
      border-color: #d9d9d9;
      color: rgba(0, 0, 0, 0.25);
      background-color: rgba(0, 0, 0, 0.04);
    }
    &.text,
    &.link {
      background-color: transparent;
      border: none;
    }
  }
}
.btn-center {
  display: block;
  text-align: center;
}
</style>
