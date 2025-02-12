<template>
  <section class="hero min-h-screen relative overflow-hidden bg-gradient-to-br from-[var(--color-brand-light)] via-[var(--color-brand-light)]/80 to-[var(--color-brand-accent)]/10">
    <!-- Complex Background Pattern -->
    <div class="absolute inset-0 opacity-10">
      <div class="absolute inset-0" style="background-image: radial-gradient(circle at 2px 2px, var(--color-brand-primary) 1px, transparent 0); background-size: 32px 32px;"></div>
      <div class="absolute inset-0 rotate-45" style="background-image: radial-gradient(circle at 2px 2px, var(--color-brand-secondary) 1px, transparent 0); background-size: 24px 24px;"></div>
    </div>

    <!-- Large Circular Glassmorphic Elements -->
    <div class="absolute inset-0 pointer-events-none overflow-hidden">
      <div class="absolute -top-32 -right-32 w-96 h-96 bg-gradient-to-br from-[var(--color-brand-primary)]/20 to-[var(--color-brand-background)]/20 rounded-full blur-3xl"></div>
      <div class="absolute -bottom-40 -left-40 w-[32rem] h-[32rem] bg-gradient-to-tr from-[var(--color-brand-accent)]/20 to-[var(--color-brand-primary)]/20 rounded-full blur-3xl"></div>
    </div>

    <!-- Enhanced Floating Elements -->
    <div class="absolute inset-0 pointer-events-none" ref="backgroundEffect">
      <!-- Geometric Shapes with Brand Colors -->
      <div class="absolute top-1/4 left-1/3 w-8 h-8 border-2 border-[var(--color-brand-primary)]/30 rounded-full animate-spin-slow"></div>
      <div class="absolute bottom-1/3 right-1/4 w-12 h-12 border-2 border-[var(--color-brand-accent)]/30 rounded-lg transform rotate-45 animate-float-slow"></div>
    </div>

    <!-- Main Content Container with Added Padding -->
    <div class="container mx-auto px-6 py-12 min-h-screen flex flex-col justify-center items-center relative z-10">
      <!-- Content Wrapper -->
      <div class="max-w-6xl w-full">
        <!-- Brand Tag - Always at top -->
        <div class="flex justify-center md:justify-start mb-8">
          <div class="inline-block bg-white rounded-full px-6 py-2 shadow-lg transform -rotate-2 border-2 border-[var(--color-brand-primary)] transition-all duration-300 hover:scale-105 hover:shadow-xl hover:rotate-0">
            <span class="text-lg font-bold brand-gradient-text">
              Dandi Digital Marketing
            </span>
          </div>
        </div>

        <!-- Responsive Layout Container -->
        <div class="flex flex-col md:flex-row md:items-center md:justify-between gap-8">
          <!-- Logo for Mobile (shown first on small screens) -->
          <div class="md:hidden flex justify-center">
            <div class="relative w-48 h-48 rounded-full overflow-hidden shadow-lg bg-gradient-to-r from-[var(--color-brand-light)]/20 to-[var(--color-brand-accent)]/20 backdrop-blur-sm">
              <img
                src="../assets/logo.png"
                alt="Logo"
                class="object-cover object-center w-full h-full rounded-full mix-blend-screen opacity-90"
              />
            </div>
          </div>

          <!-- Left Side Content -->
          <div class="md:w-1/2 text-center md:text-left">
            <!-- Main Heading -->
            <h1 class="text-5xl md:text-7xl font-black mb-6 tracking-tight">
              <span class="block brand-gradient-text">
                Your Vision
              </span>
              <span class="block text-[var(--color-brand-secondary)] mt-2">
                is Our Mission
              </span>
            </h1>

            <!-- Typewriter -->
            <div class="bg-white rounded-2xl px-6 py-4 mb-8 shadow-lg inline-block transform -rotate-1">
              <span class="text-xl md:text-2xl font-mono text-[var(--color-brand-secondary)]">
                {{ currentEmoji }} {{ displayText }}<span class="cursor">|</span>
              </span>
            </div>
          </div>

          <!-- Right Side Logo (hidden on mobile, shown on larger screens) -->
          <div class="hidden md:flex md:w-1/2 justify-end">
            <div class="relative w-64 h-64 lg:w-72 lg:h-72 rounded-full overflow-hidden shadow-lg bg-gradient-to-r from-[var(--color-brand-light)]/20 to-[var(--color-brand-background)]/20 backdrop-blur-sm">
              <img
                src="../assets/logo.png"
                alt="Logo"
                class="object-cover object-center w-full h-full rounded-full mix-blend-screen opacity-90"
              />
            </div>
          </div>
        </div>

        <!-- CTAs with added margin -->
        <div class="flex flex-col sm:flex-row gap-6 justify-center mt-12">
          <a href="#services"
             class="group inline-flex items-center justify-center px-8 py-4 rounded-2xl font-bold text-lg shadow-lg transition-all duration-300 bg-gradient-to-r from-[var(--color-brand-primary)] to-[var(--color-brand-accent)] text-white hover:shadow-xl hover:translate-y-[-2px]">
            <span>Explore Services</span>
            <svg class="w-5 h-5 ml-2 transform group-hover:translate-x-1 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6"/>
            </svg>
          </a>
          <a href="#portfolio"
             class="group inline-flex items-center justify-center px-8 py-4 rounded-2xl font-bold text-lg shadow-lg transition-all duration-300 bg-white/80 backdrop-blur-sm text-[var(--color-brand-primary)] border border-[var(--color-brand-primary)]/20 hover:shadow-xl hover:translate-y-[-2px]">
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
// Script remains the same as your original code
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

<style>
/* Utility classes for the brand colors */
.brand-gradient-text {
  background: linear-gradient(to right, var(--color-brand-primary), var(--color-brand-accent));
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