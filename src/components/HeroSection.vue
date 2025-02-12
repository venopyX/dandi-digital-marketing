<template>
  <section class="hero min-h-screen relative overflow-hidden bg-gradient-to-br from-pink-50/90 via-rose-50/80 to-purple-50/90">
    <!-- Complex Background Pattern -->
    <div class="absolute inset-0 opacity-10">
      <div class="absolute inset-0" style="background-image: radial-gradient(circle at 2px 2px, pink 1px, transparent 0); background-size: 32px 32px;"></div>
      <div class="absolute inset-0 rotate-45" style="background-image: radial-gradient(circle at 2px 2px, purple 1px, transparent 0); background-size: 24px 24px;"></div>
    </div>

    <!-- Large Circular Glassmorphic Elements -->
    <div class="absolute inset-0 pointer-events-none overflow-hidden">
      <div class="absolute -top-32 -right-32 w-96 h-96 bg-gradient-to-br from-pink-300/20 to-purple-300/20 rounded-full blur-3xl"></div>
      <div class="absolute -bottom-40 -left-40 w-[32rem] h-[32rem] bg-gradient-to-tr from-rose-300/20 to-pink-300/20 rounded-full blur-3xl"></div>
    </div>

    <!-- Enhanced Floating Elements -->
    <div class="absolute inset-0 pointer-events-none" ref="backgroundEffect">
      <!-- Original Hearts with New Positions -->
      <div class="absolute top-20 right-20 text-pink-300/80 animate-float">
        <svg width="32" height="32" viewBox="0 0 24 24" fill="currentColor">
          <path d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z"/>
        </svg>
      </div>
      <div class="absolute bottom-32 left-1/4 text-pink-300/60 animate-float-delay">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
          <path d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z"/>
        </svg>
      </div>

      <!-- Additional Stars -->
      <div class="absolute top-40 left-20 text-yellow-400/80 animate-twinkle">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
          <path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/>
        </svg>
      </div>
      <div class="absolute bottom-24 right-1/3 text-yellow-400/60 animate-twinkle-delay">
        <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
          <path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/>
        </svg>
      </div>

      <!-- Geometric Shapes -->
      <div class="absolute top-1/4 left-1/3 w-8 h-8 border-2 border-purple-300/30 rounded-full animate-spin-slow"></div>
      <div class="absolute bottom-1/3 right-1/4 w-12 h-12 border-2 border-pink-300/30 rounded-lg transform rotate-45 animate-float-slow"></div>


      <!-- Logo Space -->
      <div class="absolute top-6 left-6 w-60 h-28 flex items-center justify-center z-0">
        <!-- Logo Placeholder -->
        <div class="relative w-fit rounded-full overflow-hidden shadow-lg bg-gradient-to-r from-pink-100/20 to-purple-100/20 backdrop-blur-sm">
          <img
            src="../assets/logo.png"
            alt="Logo"
            class="object-cover object-center w-full h-full rounded-full mix-blend-screen opacity-90"
          />
        </div>
      </div>
    </div>

    <!-- Main Content Container -->
    <div class="container mx-auto px-6 min-h-screen flex flex-col justify-center items-center relative z-10">

      <!-- Content Wrapper -->
      <div class="max-w-4xl text-center">
        <!-- Brand Tag - Preserved styling with hover effect -->
        <div class="inline-block bg-white rounded-full px-6 py-2 mb-6 shadow-lg transform -rotate-2 border-2 border-pink-300 transition-all duration-300 hover:scale-105 hover:shadow-xl hover:rotate-0">
          <span class="text-lg font-bold bg-gradient text-gradient">
            Dandi Digital Marketing
          </span>
        </div>

        <!-- Main Heading -->
        <h1 class="text-6xl md:text-7xl font-black mb-6 tracking-tight">
          <span class="block bg-gradient text-gradient">
            Your Vision
          </span>
          <span class="block text-pink-400 mt-2">
            is Our Mission
          </span>
        </h1>

        <!-- Typewriter -->
        <div class="bg-white rounded-2xl px-6 py-4 mb-8 shadow-lg inline-block transform -rotate-1">
          <span class="text-2xl font-mono text-gray-700">
            {{ currentEmoji }} {{ displayText }}<span class="cursor">|</span>
          </span>
        </div>

        <!-- CTAs -->
        <div class="flex flex-col sm:flex-row gap-6 justify-center">
          <a href="#services" 
             class="group inline-flex items-center justify-center px-8 py-4 rounded-2xl font-bold text-lg shadow-lg transition-all duration-300 bg-gradient-to-r from-pink-500 to-purple-500 text-white hover:shadow-xl hover:translate-y-[-2px]">
            <span>Explore Services</span>
            <svg class="w-5 h-5 ml-2 transform group-hover:translate-x-1 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6"/>
            </svg>
          </a>
          <a href="#portfolio" 
             class="group inline-flex items-center justify-center px-8 py-4 rounded-2xl font-bold text-lg shadow-lg transition-all duration-300 bg-white/80 backdrop-blur-sm text-pink-500 border border-pink-200 hover:shadow-xl hover:translate-y-[-2px]">
            <span>View Projects</span>
            <svg class="w-5 h-5 ml-2 transform group-hover:translate-x-1 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"/>
            </svg>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'HeroSection',
  data() {
    return {
      taglines: [
        { text: 'Brand Magic', emoji: '✨' },
        { text: 'Pixel Dreams', emoji: '🎨' },
        { text: 'Growth Wonder', emoji: '💫' },
        { text: 'Story Sparkles', emoji: '🌈' },
        { text: 'Digital Joy', emoji: '⭐' },
        { text: 'Creative Fun', emoji: '🌟' }
      ],
      displayText: '',
      currentIndex: 0,
      isDeleting: false,
      typingSpeed: 100,
      deletingSpeed: 50,
    }
  },
  computed: {
    currentEmoji() {
      return this.taglines[this.currentIndex].emoji;
    }
  },
  mounted() {
    this.animateTypewriter();
    this.initParallaxEffect();
  },
  methods: {
    animateTypewriter() {
      let index = 0;
      let isDeleting = false;
      const typeEffect = () => {
        let currentText = this.taglines[this.currentIndex].text;
        
        if (isDeleting) {
          this.displayText = currentText.substring(0, this.displayText.length - 1);
        } else {
          this.displayText = currentText.substring(0, this.displayText.length + 1);
        }

        if (!isDeleting && this.displayText === currentText) {
          setTimeout(() => { isDeleting = true; typeEffect(); }, 2000);
        } else if (isDeleting && this.displayText === '') {
          isDeleting = false;
          this.currentIndex = (this.currentIndex + 1) % this.taglines.length;
          setTimeout(typeEffect, 500);
        } else {
          setTimeout(typeEffect, isDeleting ? this.deletingSpeed : this.typingSpeed);
        }
      };
      
      typeEffect();
    },
    initParallaxEffect() {
      document.addEventListener("mousemove", (e) => {
        const bg = this.$refs.backgroundEffect;
        if (bg) {
          const x = (e.clientX / window.innerWidth - 0.5) * 10;
          const y = (e.clientY / window.innerHeight - 0.5) * 10;
          bg.style.transform = `translate(${x}px, ${y}px)`;
        }
      });
    }
  }
}
</script>

<style scoped>
/* Previous styles remain */
.text-gradient {
  background: linear-gradient(to right, #ec4899, #a855f7);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

/* Enhanced Animations */
@keyframes float {
  0%, 100% { transform: translateY(0) rotate(0); }
  50% { transform: translateY(-10px) rotate(5deg); }
}

@keyframes float-delay {
  0%, 100% { transform: translateY(0) rotate(0); }
  50% { transform: translateY(-10px) rotate(-5deg); }
}

@keyframes twinkle {
  0%, 100% { opacity: 0.8; transform: scale(1); }
  50% { opacity: 0.4; transform: scale(0.9); }
}

@keyframes twinkle-delay {
  0%, 100% { opacity: 0.6; transform: scale(0.9); }
  50% { opacity: 0.3; transform: scale(1.1); }
}

@keyframes spin-slow {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

@keyframes float-slow {
  0%, 100% { transform: translateY(0) rotate(45deg); }
  50% { transform: translateY(-15px) rotate(60deg); }
}

.animate-float {
  animation: float 3s ease-in-out infinite;
}

.animate-float-delay {
  animation: float-delay 4s ease-in-out infinite;
}

.animate-twinkle {
  animation: twinkle 2s ease-in-out infinite;
}

.animate-twinkle-delay {
  animation: twinkle-delay 3s ease-in-out infinite;
}

.animate-spin-slow {
  animation: spin-slow 8s linear infinite;
}

.animate-float-slow {
  animation: float-slow 6s ease-in-out infinite;
}

.cursor {
  display: inline-block;
  animation: blink 0.8s infinite;
}

@keyframes blink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0; }
}
</style>
