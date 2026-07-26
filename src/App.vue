<template>
  <div id="app">
    <router-view v-slot="{ Component }">
      <transition name="page" mode="out-in">
        <component :is="Component" />
      </transition>
    </router-view>
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Crimson+Text:wght@400;600;700&family=Lora:wght@400;500;600&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Lora', serif;
  overflow-x: hidden;
}

/* 自定义滚动条 - 水彩风格 */
::-webkit-scrollbar {
  width: 12px;
}

::-webkit-scrollbar-track {
  background: linear-gradient(180deg, 
    rgba(147, 197, 253, 0.1) 0%,
    rgba(196, 181, 253, 0.1) 50%,
    rgba(252, 165, 165, 0.1) 100%);
}

::-webkit-scrollbar-thumb {
  background: linear-gradient(180deg, 
    rgba(147, 197, 253, 0.6) 0%,
    rgba(196, 181, 253, 0.6) 50%,
    rgba(252, 165, 165, 0.6) 100%);
  border-radius: 10px;
  border: 2px solid transparent;
  background-clip: padding-box;
}

::-webkit-scrollbar-thumb:hover {
  background: linear-gradient(180deg, 
    rgba(147, 197, 253, 0.8) 0%,
    rgba(196, 181, 253, 0.8) 50%,
    rgba(252, 165, 165, 0.8) 100%);
  background-clip: padding-box;
}

/* 翻页动画 */
.page-enter-active {
  animation: page-in 1.2s ease-out;
}

.page-leave-active {
  animation: page-out 0.8s ease-in;
}

@keyframes page-in {
  0% {
    transform: perspective(1000px) rotateY(-90deg);
    opacity: 0;
  }
  100% {
    transform: perspective(1000px) rotateY(0deg);
    opacity: 1;
  }
}

@keyframes page-out {
  0% {
    transform: perspective(1000px) rotateY(0deg);
    opacity: 1;
  }
  100% {
    transform: perspective(1000px) rotateY(90deg);
    opacity: 0;
  }
}
</style>