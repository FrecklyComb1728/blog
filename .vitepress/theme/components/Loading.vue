<template>
  <Teleport to="body">
    <Transition name="fade" mode="out-in">
      <div v-if="loadingStatus" class="loading" @click="loadingStatus = false">
        <img :src="theme.siteMeta.logo" class="logo" alt="loading-logo" />
        <span :class="['tip', { show: showTip }]"> 一直显示？点击任意区域即可关闭 </span>
      </div>
    </Transition>
  </Teleport>
</template>

<script setup>
import { storeToRefs } from 'pinia';
import { mainStore } from '@/store';

const store = mainStore();
const { theme } = useData();
const { loadingStatus } = storeToRefs(store);

// 显示提示
const showTip = ref(false);
const showTimeOut = ref(null);

// 监听加载状态
watch(
  () => loadingStatus.value,
  (val) => {
    if (val) {
      showTimeOut.value = setTimeout(() => {
        showTip.value = true;
      }, 3000);
    } else {
      showTip.value = false;
      clearTimeout(showTimeOut.value);
    }
  },
);

// 确保加载动画能在页面加载时正确结束
onMounted(() => {
  // 如果需要初始化 loadingStatus 为 true，可以在这里设置
  loadingStatus.value = true;

  // 可选：如果希望在页面加载后 3 秒关闭加载动画
  // setTimeout(() => {
  //   loadingStatus.value = false;
  // }, 3000);
});

onBeforeUnmount(() => {
  clearTimeout(showTimeOut.value);
});
</script>

<style lang="scss" scoped>
.loading {
  position: fixed;
  top: 0;
  left: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 100vw;
  height: 100vh;
  background-color: var(--main-card-background);
  z-index: 9999;
  .logo {
    width: 100px;
    height: 100px;
    animation: loading 2s infinite;
  }
  .tip {
    position: absolute;
    bottom: 2rem;
    font-size: 14px;
    opacity: 0;
    transition: opacity 0.3s;
    &.show {
      opacity: 0.6;
    }
  }
}
</style>
