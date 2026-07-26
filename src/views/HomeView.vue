<template>
  <div class="home-container">
    <WatercolorBackground />
    <CoverPage v-if="!showLetter" @enter="onEnter" />
    <LetterPage v-else :paragraphs="paragraphs" />
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
    const paragraphs = ref([])

    const onEnter = (decrypted) => {
      paragraphs.value = decrypted
      showLetter.value = true
    }

    return {
      showLetter,
      paragraphs,
      onEnter
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