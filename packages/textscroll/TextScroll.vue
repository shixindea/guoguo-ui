<script setup lang="ts">
import { ref, computed, watch, onMounted, type CSSProperties } from 'vue'
import { rafTimeout, cancelRaf } from '../utils'
interface Text {
  title: string // 文字标题
  link?: string // 跳转链接
}
interface Props {
  scrollText: Text[] | Text // 滚动文字数组，single 为 true 时，类型为 Text
  single?: boolean // 是否启用单条文字滚动效果，只支持水平文字滚动，为 true 时，amount 自动设为 1
  width?: number | string // 滚动区域宽度，单位px
  height?: number // 滚动区域高度，单位px
  boardStyle?: CSSProperties // 滚动区域样式，优先级低于 width、height
  textStyle?: CSSProperties // 滚动文字样式
  amount?: number // 滚动区域展示条数，水平滚动时生效
  gap?: number // 水平滚动文字各列间距或垂直滚动文字两边的边距，单位px
  interval?: number // 水平滚动动画执行时间间隔，单位ms，水平滚动时生效
  step?: number // 水平滚动动画每次执行时移动距离，单位px，水平滚动时生效，与 interval 配合控制滚动速度
  vertical?: boolean // 是否垂直滚动
  verticalInterval?: number // 垂直文字滚动时间间隔，单位ms，垂直滚动时生效
}
const props = withDefaults(defineProps<Props>(), {
  scrollText: () => [],
  single: false,
  width: '100%',
  height: 50,
  boardStyle: () => ({}),
  textStyle: () => ({}),
  amount: 4,
  gap: 20,
  interval: 10,
  step: 1,
  vertical: false,
  verticalInterval: 3000
})
const textData = computed(() => {
  if (props.single) {
    return [props.scrollText, props.scrollText]
  } else {
    return [...(props.scrollText as Text[])]
  }
})
const textAmount = computed(() => {
  return textData.value.length || 0
})
const totalWidth = computed(() => {
  // 文字滚动区域总宽度
  if (typeof props.width === 'number') {
    return props.width + 'px'
  } else {
    return props.width
  }
})
const displayAmount = computed(() => {
  if (props.single) {
    return 1
  } else {
    return props.amount
  }
})
const left = ref(0)
const horizontalMoveRaf = ref() // 水平滚动引用
const verticalMoveRaf = ref() // 垂直滚动引用
const origin = ref(true)
const horizonRef = ref()
const distance = ref(0) // 每条滚动文字移动距离
watch(
  () => [
    textData,
    props.width,
    props.amount,
    props.gap,
    props.step,
    props.interval,
    props.vertical,
    props.verticalInterval
  ],
  () => {
    if (!props.vertical) {
      distance.value = getDistance() // 获取每列文字宽度
    } else {
      origin.value = true
    }
    horizontalMoveRaf.value && cancelRaf(horizontalMoveRaf.value)
    verticalMoveRaf.value && cancelRaf(verticalMoveRaf.value)
    startMove() // 开始滚动
  },
  {
    deep: true, // 强制转成深层侦听器
    flush: 'post'
  }
)
onMounted(() => {
  if (!props.vertical) {
    distance.value = getDistance() // 获取每列文字宽度
  }
  startMove() // 开始滚动
})
function getDistance(): number {
  return parseFloat((horizonRef.value.offsetWidth / displayAmount.value).toFixed(2))
}
function startMove() {
  if (props.vertical) {
    if (textAmount.value > 1) {
      verticalMoveRaf.value && cancelRaf(verticalMoveRaf.value)
      verticalMove() // 垂直滚动
    }
  } else {
    if (textAmount.value > displayAmount.value) {
      // 超过 amount 条开始滚动
      horizontalMoveRaf.value && cancelRaf(horizontalMoveRaf.value)
      horizonMove() // 水平滚动
    }
  }
}
function horizonMove() {
  horizontalMoveRaf.value = rafTimeout(
    () => {
      if (left.value >= distance.value) {
        textData.value.push(textData.value.shift() as Text) // 将第一条数据放到最后
        left.value = 0
      } else {
        left.value += props.step // 每次移动step（px）
      }
    },
    props.interval,
    true
  )
}
function stopMove() {
  // 暂停动画
  if (props.vertical) {
    verticalMoveRaf.value && cancelRaf(verticalMoveRaf.value)
  } else {
    horizontalMoveRaf.value && cancelRaf(horizontalMoveRaf.value)
  }
}
const emit = defineEmits(['click'])
function onClick(text: Text) {
  // 通知父组件点击的标题
  emit('click', text)
}
const actIndex = ref(0)
function verticalMove() {
  verticalMoveRaf.value = rafTimeout(
    () => {
      if (origin.value) {
        origin.value = false
      }
      actIndex.value = (actIndex.value + 1) % textAmount.value
      verticalMove()
    },
    origin.value ? props.verticalInterval : props.verticalInterval + 1000
  )
}
</script>
<template>
  <div
    v-if="!vertical"
    ref="horizonRef"
    class="m-slider-horizon"
    :style="[boardStyle, `height: ${height}px; width: ${totalWidth}; --gap: ${gap}px;`]"
  >
    <div class="m-scroll-view" :style="`will-change: transform; transform: translateX(${-left}px);`">
      <a
        class="u-slide-title"
        :style="[textStyle, `width: ${distance - gap}px;`]"
        v-for="(text, index) in <Text[]>textData"
        :key="index"
        :title="text.title"
        :href="text.link ? text.link : 'javascript:;'"
        :target="text.link ? '_blank' : '_self'"
        @mouseenter="stopMove"
        @mouseleave="startMove"
        @click="onClick(text)"
      >
        {{ text.title || '--' }}
      </a>
    </div>
  </div>
  <div
    v-else
    class="m-slider-vertical"
    :style="[
      boardStyle,
      `height: ${height}px; width: ${totalWidth}; --enter-move: ${height}px; --leave-move: ${-height}px; --gap: ${gap}px;`
    ]"
  >
    <TransitionGroup name="slide">
      <div class="m-scroll-view" v-for="(text, index) in <Text[]>textData" :key="index" v-show="actIndex === index">
        <a
          class="u-slider"
          :style="textStyle"
          :title="text.title"
          :href="text.link ? text.link : 'javascript:;'"
          :target="text.link ? '_blank' : '_self'"
          @mouseenter="stopMove"
          @mouseleave="startMove"
          @click="onClick(text)"
        >
          {{ text.title || '--' }}
        </a>
      </div>
    </TransitionGroup>
  </div>
</template>
<style lang="less" scoped>
// 水平滚动
.m-slider-horizon {
  overflow: hidden;
  box-shadow: 0px 0px 5px #d3d3d3;
  border-radius: 6px;
  background-color: #fff;
  .m-scroll-view {
    height: 100%;
    display: inline-flex;
    align-items: center;
    gap: var(--gap);
    padding-left: var(--gap);
    .u-slide-title {
      font-size: 16px;
      font-weight: 400;
      color: rgba(0, 0, 0, 0.88);
      line-height: 1.57;
      overflow: hidden;
      text-overflow: ellipsis;
      white-space: nowrap;
      cursor: pointer;
      transition: color 0.3s;
      &:hover {
        color: @themeColor;
      }
    }
  }
}
// 垂直滚动
.slide-enter-active,
.slide-leave-active {
  transition: all 1s ease;
}
.slide-enter-from {
  transform: translateY(var(--enter-move)) scale(0.5);
  opacity: 0;
}
.slide-leave-to {
  transform: translateY(var(--leave-move)) scale(0.5);
  opacity: 0;
}
.m-slider-vertical {
  overflow: hidden;
  box-shadow: 0px 0px 5px #d3d3d3;
  border-radius: 6px;
  background-color: #fff;
  position: relative;
  .m-scroll-view {
    position: absolute;
    left: 0;
    right: 0;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 0 var(--gap);
    .u-slider {
      font-size: 16px;
      font-weight: 400;
      color: rgba(0, 0, 0, 0.88);
      line-height: 1.57;
      overflow: hidden;
      white-space: nowrap;
      text-overflow: ellipsis;
      cursor: pointer;
      transition: color 0.3s;
      &:hover {
        color: @themeColor;
      }
    }
  }
}
</style>
