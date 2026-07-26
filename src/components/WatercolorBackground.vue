<template>
  <div class="scroll-bg">
    <div class="texture-layer"></div>
  </div>
</template>

<script>
export default {
  name: 'WatercolorBackground'
}
</script>

<style scoped>
.scroll-bg {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
  background: linear-gradient(
    135deg,
    #8b7355 0%,
    #a0826d 50%,
    #8b7355 100%
  );
}

.texture-layer {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: 
    repeating-linear-gradient(
      90deg,
      transparent,
      transparent 2px,
      rgba(0, 0, 0, 0.03) 2px,
      rgba(0, 0, 0, 0.03) 4px
    );
  opacity: 0.3;
}
</style>