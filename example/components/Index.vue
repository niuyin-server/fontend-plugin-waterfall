<template>
  <div class="h-screen flex overflow-hidden">
    <div class="flex-auto overflow-y-auto scroller">
      <WaterfallList :options="options" @cardClick="dialogVisible = true"/>
    </div>
  </div>
</template>

<script setup lang="ts">
import {reactive, ref} from 'vue'
import error from '../assets/error.png'
import loading from '../assets/loading.png'
import WaterfallList from './WaterfallList.vue'

const options = reactive({
  // 唯一key值
  rowKey: 'id',
  // 卡片之间的间隙
  gutter: 10,
  // 是否有周围的gutter
  hasAroundGutter: true,
  // 卡片在PC上的宽度
  width: 460,
  // 自定义行显示个数，主要用于对移动端的适配
  breakpoints: {
    3840: {
      // 4K下
      rowPerView: 8,
    },
    2560: {
      // 2K下
      rowPerView: 7,
    },
    1920: {
      // 2K下
      rowPerView: 6,
    },
    1600: {
      // 2K下
      rowPerView: 5,
    },
    1366: {
      // 2K下
      rowPerView: 4,
    },
    820: {
      // 当屏幕宽度小于等于800
      rowPerView: 3,
    },
    640: {
      // 当屏幕宽度小于等于500
      rowPerView: 2,
    },
  },
  // 动画效果
  animationEffect: 'animate__fadeInUp',
  // 动画时间
  animationDuration: 500,
  // 动画延迟
  animationDelay: 100,
  // 背景色
  backgroundColor: '#2C2E3A',
  // imgSelector
  imgSelector: 'src.original',
  // 加载配置
  loadProps: {
    loading,
    error,
  },
  // 是否懒加载
  lazyload: false,
  align: 'center',
  crossOrigin: true,
})

const dialogVisible = ref(false)
</script>

<style scoped>
.scroller::-webkit-scrollbar {
  z-index: 10;
  cursor: pointer;
  background-color: #2C2E3A;
  overflow: hidden;
  width: 8px;
  height: 1px;
}

.scroller::-webkit-scrollbar-button {
  display: none;
}

.scroller::-webkit-scrollbar-thumb {
  background: rgba(239, 33, 112, 0.5);
  cursor: pointer;
  border-radius: 5px;
}

.scroller::-webkit-scrollbar-corner {
  display: none;
}

.scroller::-webkit-resizer {
  display: none;
}

</style>
