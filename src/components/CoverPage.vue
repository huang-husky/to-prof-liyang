<template>
  <div class="password-page">
    <div class="scroll-container">
      <div class="scroll-top"></div>
      
      <div class="scroll-content">
        <h1 class="seal-title">致李旸老师</h1>
        
        <div class="password-box">
          <div class="lock-icon">🔒</div>
          <input 
            v-model="password" 
            type="password" 
            class="password-input" 
            placeholder="please enter the password"
            @keyup.enter="checkPassword"
          />
          <button class="open-btn" @click="checkPassword">
            Open
          </button>
          <p v-if="errorMsg" class="error-msg">{{ errorMsg }}</p>
          <p class="hint">🎇</p>
        </div>
      </div>
      
      <div class="scroll-bottom"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CoverPage',
  emits: ['enter'],
  data() {
    return {
      password: '',
      errorMsg: '',
      correctPassword: 'drliyang'
    }
  },
  methods: {
    checkPassword() {
      if (this.password === this.correctPassword) {
        this.errorMsg = ''
        this.$emit('enter')
      } else {
        this.errorMsg = 'Sorry, please try again.'
        this.password = ''
      }
    }
  }
}
</script>

<style scoped>
.password-page {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  padding: 40px 20px;
  width: 100vw;
  position: fixed;
  top: 0;
  left: 0;
}

.scroll-container {
  width: 100%;
  max-width: 500px;
  margin: 0 auto;
  animation: float 1.5s ease-in-out;
}

@keyframes float {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.scroll-top,
.scroll-bottom {
  height: 30px;
  background: linear-gradient(to bottom, #654321, #5c3d1f);
  border-radius: 15px 15px 0 0;
  box-shadow: 
    inset 0 2px 5px rgba(0, 0, 0, 0.3),
    0 2px 8px rgba(0, 0, 0, 0.3);
  position: relative;
}

.scroll-top::before,
.scroll-bottom::before {
  content: '';
  position: absolute;
  left: 10%;
  right: 10%;
  top: 50%;
  height: 3px;
  background: rgba(0, 0, 0, 0.2);
  transform: translateY(-50%);
}

.scroll-bottom {
  border-radius: 0 0 15px 15px;
  transform: rotate(180deg);
}

.scroll-content {
  background: linear-gradient(
    to bottom,
    #f4e4c1 0%,
    #f5e6c8 50%,
    #f4e4c1 100%
  );
  padding: 50px 40px;
  box-shadow: 
    inset 0 0 50px rgba(139, 115, 85, 0.1),
    0 10px 30px rgba(0, 0, 0, 0.3);
  border-left: 3px solid #8b7355;
  border-right: 3px solid #8b7355;
  position: relative;
}

.scroll-content::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-image: 
    repeating-linear-gradient(
      0deg,
      transparent,
      transparent 20px,
      rgba(139, 115, 85, 0.05) 20px,
      rgba(139, 115, 85, 0.05) 21px
    );
  pointer-events: none;
}

.seal-title {
  font-family: 'Songti SC', 'SimSun', serif;
  font-size: 2.5rem;
  font-weight: 400;
  color: #3d2817;
  text-align: center;
  margin-bottom: 0.5rem;
  letter-spacing: 0.3em;
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.1);
}

.seal-subtitle {
  font-family: 'Songti SC', 'SimSun', serif;
  font-size: 1rem;
  color: #6b4423;
  text-align: center;
  margin-bottom: 2.5rem;
}

.password-box {
  text-align: center;
}

.lock-icon {
  font-size: 3rem;
  margin-bottom: 1.5rem;
  opacity: 0.6;
}

.password-input {
  width: 100%;
  max-width: 300px;
  padding: 12px 20px;
  font-size: 1rem;
  font-family: 'Songti SC', 'SimSun', serif;
  border: 2px solid #8b7355;
  border-radius: 4px;
  background: rgba(255, 255, 255, 0.8);
  color: #3d2817;
  text-align: center;
  letter-spacing: 0.3em;
  margin-bottom: 1.5rem;
  transition: all 0.3s ease;
}

.password-input:focus {
  outline: none;
  border-color: #6b4423;
  box-shadow: 0 0 0 3px rgba(139, 115, 85, 0.2);
}

.password-input::placeholder {
  color: #a0826d;
  letter-spacing: 0.1em;
}

.open-btn {
  width: 100%;
  max-width: 300px;
  padding: 12px 30px;
  font-size: 1.1rem;
  font-family: 'Songti SC', 'SimSun', serif;
  color: #f4e4c1;
  background: linear-gradient(135deg, #6b4423, #8b7355);
  border: none;
  border-radius: 4px;
  cursor: pointer;
  letter-spacing: 0.3em;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
  transition: all 0.3s ease;
}

.open-btn:hover {
  background: linear-gradient(135deg, #5c3d1f, #6b4423);
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
  transform: translateY(-2px);
}

.open-btn:active {
  transform: translateY(0);
}

.error-msg {
  color: #c4442f;
  font-size: 0.9rem;
  margin-top: 1rem;
  font-family: 'Songti SC', 'SimSun', serif;
}

.hint {
  color: #8b7355;
  font-size: 0.85rem;
  margin-top: 1.5rem;
  font-family: 'Songti SC', 'SimSun', serif;
  opacity: 0.7;
}

@media (max-width: 768px) {
  .seal-title {
    font-size: 2rem;
  }
  
  .scroll-content {
    padding: 40px 30px;
  }
}
/* 密码框获得焦点时的光晕 */
.password-input:focus {
  outline: none;
  border-color: #6b4423;
  box-shadow: 
    0 0 0 3px rgba(139, 115, 85, 0.2),
    0 0 20px rgba(139, 115, 85, 0.3);
  animation: input-glow 2s ease-in-out infinite;
}

@keyframes input-glow {
  0%, 100% {
    box-shadow: 
      0 0 0 3px rgba(139, 115, 85, 0.2),
      0 0 20px rgba(139, 115, 85, 0.3);
  }
  50% {
    box-shadow: 
      0 0 0 3px rgba(139, 115, 85, 0.3),
      0 0 30px rgba(139, 115, 85, 0.4);
  }
}

/* 锁头轻微摇晃 */
.lock-icon {
  font-size: 3rem;
  margin-bottom: 1.5rem;
  opacity: 0.6;
  animation: lock-shake 3s ease-in-out infinite;
}

@keyframes lock-shake {
  0%, 100% {
    transform: rotate(0deg);
  }
  25% {
    transform: rotate(-5deg);
  }
  75% {
    transform: rotate(5deg);
  }
}
</style>