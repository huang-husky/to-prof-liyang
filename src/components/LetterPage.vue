<template>
  <div class="letter-page">
    <div class="scroll-wrapper">
      <div class="scroll-rod scroll-rod-left"></div>
      <div class="scroll-rod scroll-rod-right"></div>
      
      <div class="scroll-paper">
        <div class="paper-edge paper-edge-top"></div>
        
        <div class="letter-content">
          <div class="red-seal">
            <div class="seal-stamp">亲启</div>
          </div>
          
          <h2 class="letter-title">致李旸老师</h2>
          
          <div class="letter-body">
            <p v-for="(paragraph, index) in paragraphs" :key="index" class="paragraph">
              {{ paragraph }}
            </p>
          </div>
          
          <div class="signature">
            <p>您的学生</p>
            <p class="name">黄湘淇 敬上</p>
            <p class="date">二〇二五年十二月三十日</p>
          </div>
        </div>
        
        <div class="paper-edge paper-edge-bottom"></div>
      </div>
    </div>
    
    <!-- 音乐控制按钮 -->
    <button class="music-btn" @click="toggleMusic" :title="isPlaying ? '暂停音乐' : '播放音乐'">
      <span v-if="isPlaying" class="music-icon">⏸</span>
      <span v-else class="music-icon">♪</span>
    </button>
    
    <!-- 音频元素 -->
    <audio ref="bgMusic" loop>
      <source src="/music.mp3" type="audio/mpeg">
    </audio>
  </div>
</template>

<script>
export default {
  name: 'LetterPage',
  data() {
    return {
      isPlaying: false,
    paragraphs: [
        '尊敬的李老师：',
        '您好！',
        '一学期的宏观经济学课程接近尾声，想起这几个月的课堂时光，心中有些话想要说给您听。',
        '初见您时，便觉得您身上有种难得的气质——年轻，却又沉稳。您没有拘泥于指定的教材，而是带我们走进曼昆那本经典著作的世界；您也不只是讲授书本上的理论，而是常常信手拈来当下的时事政治，让那些原本抽象的经济学概念在现实中有了温度和生命。您不止一次地建议我们多读新闻、多了解时事政治，还推荐了《联合早报》这样的刊物。起初我并不太理解，但随着课程的深入，我渐渐明白了您的用心。',
        '这一学期的学习，于我而言，像是推开了一扇新的窗。我得以浅窥世界经济运行的奥秘，开始理解那些曾经只是模糊概念的社会现象——为什么物价会上涨，为什么国家要调控房地产，为什么货币政策的一个微调就能牵动整个市场的神经。那些每天发生在我们身边的新闻，突然有了理论的支撑和解释的逻辑。我开始明白，中国为什么要在某个节点出台某项经济政策，那背后是怎样的考量和权衡。经济学不再是纸面上的公式和曲线,而是实实在在地帮我理解这个世界的工具。',
        '有一件事，我一直记在心里。您在完成教学任务后，本可以就此收笔，却还想为我们打开另一扇窗——那个DAD-DAS模型。您说，这对想要更进一步的同学会有帮助。那些全英文的PPT，想必您花了不少心思。可那天的教室里，回应您的却是一片安静。期末将至，大家的心思大概都在考试范围之内。我坐在座位上，看着讲台上的您，心里五味杂陈。',
        '我知道那些内容的价值，知道您想给我们的不仅仅是一张漂亮的成绩单，而是一把能打开更广阔世界的钥匙。只是现实常常让人无奈——时间有限，精力分散，我们在该追寻远方的年纪，却不得不先应付眼前的考试。这学期里，我大多数时候都在认真听讲，课堂上也很少碰手机，但如果说遗憾，大概是没能抽出更多时间去深入钻研每章内容，也没能提出什么让您眼前一亮的问题。',
        '不过，我想这也许就是师生缘分的常态吧。我们不是每一次都能恰好接住老师抛来的球，也不是每一堂课都能完美回应老师的期待。但那些被记住的瞬间、那些被播下的种子，总会在某个时刻发芽。也许在未来的某一天，当我们真正需要那些知识时，会想起您曾经打开的那扇窗。',
        '感谢您这一学期的教导，让我不仅学到了知识，更学会了用经济学的眼光看世界。愿您在讲台上，继续保持那份对教育的热忱。也祝您工作顺利，新年快乐！感恩相遇！',
      ]
    }
  },
  mounted() {
    // 设置音量（0.0 - 1.0）
    this.$refs.bgMusic.volume = 0.2
  },
  methods: {
    toggleMusic() {
      const audio = this.$refs.bgMusic
      if (this.isPlaying) {
        audio.pause()
        this.isPlaying = false
      } else {
        audio.play()
          .then(() => {
            this.isPlaying = true
          })
          .catch(err => {
            console.error('播放失败:', err)
            alert('播放失败，请检查音频文件')
          })
      }
    }
  }
}
</script>

<style scoped>
.letter-page {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  width: 100%;
  padding: 60px 20px;
  animation: scroll-unfold 1.2s ease-out;
}

@keyframes scroll-unfold {
  from {
    opacity: 0;
    transform: scaleX(0.3);
  }
  to {
    opacity: 1;
    transform: scaleX(1);
  }
}

.scroll-wrapper {
  position: relative;
  max-width: 900px;
  width: 100%;
  margin: 0 auto;
}

.scroll-rod {
  position: absolute;
  width: 30px;
  height: 100%;
  background: linear-gradient(to right, #5c3d1f, #654321, #5c3d1f);
  border-radius: 15px;
  box-shadow: 
    inset 0 0 10px rgba(0, 0, 0, 0.3),
    2px 0 8px rgba(0, 0, 0, 0.3);
  z-index: 2;
  transition: transform 0.3s ease;
}

.scroll-rod-left {
  left: -15px;
}

.scroll-rod-right {
  right: -15px;
}

.scroll-wrapper:hover .scroll-rod-left {
  transform: translateX(-2px);
}

.scroll-wrapper:hover .scroll-rod-right {
  transform: translateX(2px);
}

.scroll-paper {
  background: linear-gradient(
    to bottom,
    #f4e4c1 0%,
    #f5e6c8 50%,
    #f4e4c1 100%
  );
  box-shadow: 
    0 10px 40px rgba(0, 0, 0, 0.3),
    inset 0 0 100px rgba(139, 115, 85, 0.1);
  position: relative;
  animation: paper-breathe 4s ease-in-out infinite;
}

@keyframes paper-breathe {
  0%, 100% {
    box-shadow: 
      0 10px 40px rgba(0, 0, 0, 0.3),
      inset 0 0 100px rgba(139, 115, 85, 0.1);
  }
  50% {
    box-shadow: 
      0 15px 50px rgba(0, 0, 0, 0.35),
      inset 0 0 120px rgba(139, 115, 85, 0.15);
  }
}

.paper-edge {
  height: 40px;
  background: linear-gradient(to bottom, #8b7355, #6b4423);
  position: relative;
}

.paper-edge-top {
  border-radius: 8px 8px 0 0;
}

.paper-edge-bottom {
  border-radius: 0 0 8px 8px;
}

.paper-edge::before {
  content: '';
  position: absolute;
  left: 5%;
  right: 5%;
  top: 50%;
  height: 4px;
  background: rgba(0, 0, 0, 0.2);
  transform: translateY(-50%);
  border-radius: 2px;
}

.letter-content {
  padding: 60px 80px;
  background-image: 
    repeating-linear-gradient(
      0deg,
      transparent,
      transparent 24px,
      rgba(139, 115, 85, 0.08) 24px,
      rgba(139, 115, 85, 0.08) 25px
    );
  position: relative;
}

.red-seal {
  position: absolute;
  top: 30px;
  right: 60px;
  width: 80px;
  height: 80px;
  background: radial-gradient(circle, #c4442f, #a0321f);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 15px rgba(196, 68, 47, 0.4);
  transform: rotate(-15deg);
  animation: seal-drop 1.5s cubic-bezier(0.34, 1.56, 0.64, 1) 0.5s backwards;
}

@keyframes seal-drop {
  0% {
    opacity: 0;
    transform: translateY(-100px) rotate(-15deg) scale(0.5);
  }
  60% {
    transform: translateY(5px) rotate(-15deg) scale(1.1);
  }
  100% {
    opacity: 1;
    transform: translateY(0) rotate(-15deg) scale(1);
  }
}

.seal-stamp {
  font-family: 'Songti SC', 'SimSun', serif;
  font-size: 1.2rem;
  color: #f4e4c1;
  text-align: center;
  line-height: 1.4;
  font-weight: 600;
  letter-spacing: 0.1em;
}

.letter-title {
  font-family: 'Songti SC', 'SimSun', serif;
  font-size: 2.2rem;
  font-weight: 400;
  color: #3d2817;
  text-align: center;
  margin-bottom: 40px;
  letter-spacing: 0.4em;
  padding-bottom: 20px;
  border-bottom: 2px solid rgba(139, 115, 85, 0.3);
  position: relative;
  overflow: hidden;
}

.letter-title::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: -100%;
  width: 100%;
  height: 2px;
  background: linear-gradient(to right, transparent, #8b7355, transparent);
  animation: title-underline 2s ease-in-out 1s forwards;
}

@keyframes title-underline {
  to {
    left: 100%;
  }
}

.letter-body {
  font-family: 'Songti SC', 'SimSun', serif;
  font-size: 1.1rem;
  line-height: 2.4;
  color: #3d2817;
}

.paragraph {
  margin-bottom: 1.8em;
  text-indent: 2em;
  text-align: justify;
  opacity: 0;
  animation: text-fade-in 0.8s ease forwards;
}

.paragraph:nth-child(1) { animation-delay: 0.3s; }
.paragraph:nth-child(2) { animation-delay: 0.5s; }
.paragraph:nth-child(3) { animation-delay: 0.7s; }
.paragraph:nth-child(4) { animation-delay: 0.9s; }
.paragraph:nth-child(5) { animation-delay: 1.1s; }

@keyframes text-fade-in {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.signature {
  margin-top: 60px;
  text-align: right;
  font-family: 'Songti SC', 'SimSun', serif;
  color: #5c3d1f;
  line-height: 2.2;
  opacity: 0;
  animation: signature-fade 1s ease forwards 1.5s;
}

@keyframes signature-fade {
  from {
    opacity: 0;
    transform: translateX(20px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

.signature .name {
  font-size: 1.2rem;
  color: #3d2817;
  margin: 8px 0;
  font-weight: 500;
}

.signature .date {
  font-size: 1rem;
  color: #6b4423;
}

/* 音乐播放按钮 */
.music-btn {
  position: fixed;
  bottom: 40px;
  right: 40px;
  width: 60px;
  height: 60px;
  border-radius: 50%;
  background: linear-gradient(135deg, #8b7355, #6b4423);
  border: 3px solid #f4e4c1;
  color: #f4e4c1;
  font-size: 1.5rem;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 
    0 4px 15px rgba(0, 0, 0, 0.3),
    inset 0 2px 5px rgba(255, 255, 255, 0.2);
  transition: all 0.3s ease;
  z-index: 100;
  animation: music-btn-pulse 2s ease-in-out infinite;
}

.music-btn:hover {
  transform: scale(1.1);
  box-shadow: 
    0 6px 20px rgba(0, 0, 0, 0.4),
    inset 0 2px 5px rgba(255, 255, 255, 0.3);
}

.music-btn:active {
  transform: scale(0.95);
}

@keyframes music-btn-pulse {
  0%, 100% {
    box-shadow: 
      0 4px 15px rgba(0, 0, 0, 0.3),
      inset 0 2px 5px rgba(255, 255, 255, 0.2);
  }
  50% {
    box-shadow: 
      0 6px 20px rgba(139, 115, 85, 0.5),
      inset 0 2px 5px rgba(255, 255, 255, 0.3);
  }
}

.music-icon {
  display: inline-block;
  animation: icon-rotate 3s linear infinite;
}

@keyframes icon-rotate {
  0%, 100% {
    transform: rotate(0deg);
  }
  25% {
    transform: rotate(-10deg);
  }
  75% {
    transform: rotate(10deg);
  }
}

@media (max-width: 768px) {
  .scroll-rod {
    width: 20px;
  }
  
  .scroll-rod-left {
    left: -10px;
  }
  
  .scroll-rod-right {
    right: -10px;
  }
  
  .letter-content {
    padding: 40px 30px;
  }
  
  .red-seal {
    width: 60px;
    height: 60px;
    right: 30px;
  }
  
  .seal-stamp {
    font-size: 0.9rem;
  }
  
  .letter-title {
    font-size: 1.8rem;
  }
  
  .letter-body {
    font-size: 1rem;
  }
  
  .music-btn {
    width: 50px;
    height: 50px;
    bottom: 20px;
    right: 20px;
    font-size: 1.2rem;
  }
}
</style>