<template>
  <div class="home-container">
    <WatercolorBackground />
    <CoverPage v-if="!showLetter" @enter="showLetter = true" />
    <LetterPage v-else />
  </div>
</template>

<script>
import { ref } from 'vue'
import WatercolorBackground from '@/components/WatercolorBackground.vue'
import CoverPage from '@/components/CoverPage.vue'
import LetterPage from '@/components/LetterPage.vue'

export default {
  name: 'HomePage',
  components: {
    WatercolorBackground,
    CoverPage,
    LetterPage
  },
  setup() {
    const showLetter = ref(false)
    
    return {
      showLetter
    }
  }
}
</script>

<style scoped>
.home-container {
  position: relative;
  width: 100vw;
  min-height: 100vh;
  overflow: hidden;
}
</style>