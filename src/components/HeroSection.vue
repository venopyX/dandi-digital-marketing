<template>
  <section class="hero relative min-h-screen bg-[#FFDE59] overflow-hidden pt-20">
    <!-- Brutalist Background Pattern -->
    <div class="absolute inset-0 bg-pattern opacity-5"></div>
    
    <!-- Content Container -->
    <div class="container mx-auto px-6 min-h-screen flex flex-col justify-center relative">
      <!-- Geometric Shapes -->
      <div class="absolute top-40 right-10 w-40 h-40 bg-[#FF3366] rotate-12 border-[6px] border-black shadow-brutal z-0"></div>
      <div class="absolute bottom-20 left-10 w-32 h-32 bg-[#00C6BE] -rotate-12 border-[6px] border-black shadow-brutal z-0"></div>
      <div class="absolute top-60 left-[40%] w-24 h-24 bg-[#4D27F7] rotate-45 border-[6px] border-black shadow-brutal z-0"></div>
      
      <!-- Main Content -->
      <div class="max-w-4xl relative z-10">
        <!-- Brand Tag -->
        <div class="inline-block mb-8 px-6 py-3 bg-black text-white text-xl font-mono transform -rotate-2 border-[6px] border-black shadow-brutal">
          Dandi Digital Marketing
        </div>
        
        <!-- Main Headline -->
        <h1 class="text-6xl md:text-8xl font-black mb-8 leading-tight text-black relative">
          <span class="bg-white inline-block px-4 py-2 border-[6px] border-black shadow-brutal transform -rotate-1 mb-4">Your Vision</span> <br/>
          <span class="relative inline-block bg-[#FF3366] text-white px-4 py-2 border-[6px] border-black shadow-brutal transform rotate-1">
            is Our Mission
          </span>
        </h1>
        
        <!-- Rotating Tagline -->
        <div class="typewriter-container mb-12 bg-[#00C6BE] inline-block px-6 py-3 border-[6px] border-black shadow-brutal transform -rotate-1">
          <h2 class="text-2xl md:text-3xl font-bold text-white font-mono">
            {{ currentTagline }}
          </h2>
        </div>
        
        <!-- CTA Buttons -->
        <div class="flex flex-wrap gap-8">
          <a href="#services" class="cta-primary px-8 py-4 bg-[#4D27F7] text-white text-xl font-bold border-[6px] border-black shadow-brutal hover:translate-x-2 hover:-translate-y-2 transition-transform">
            Explore Services
          </a>
          <a href="#portfolio" class="cta-secondary px-8 py-4 bg-white text-black text-xl font-bold border-[6px] border-black shadow-brutal hover:translate-x-2 hover:-translate-y-2 transition-transform">
            View Projects
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
        'Brand Sculpting',
        'Pixel Alchemy',
        'Conversion Engineering',
        'Visual Storytelling',
        'Digital Growth Architect',
        'Visual Identity Forge'
      ],
      currentTagline: 'Brand Sculpting',
      taglineIndex: 0
    }
  },
  mounted() {
    this.startTaglineRotation();
  },
  methods: {
    startTaglineRotation() {
      setInterval(() => {
        this.taglineIndex = (this.taglineIndex + 1) % this.taglines.length;
        this.currentTagline = this.taglines[this.taglineIndex];
      }, 3000);
    }
  }
}
</script>

<style scoped>
/* Neo-Brutalist Base Styles */
.bg-pattern {
  background-image: radial-gradient(#000 2px, transparent 2px);
  background-size: 48px 48px;
}

.shadow-brutal {
  box-shadow: 8px 8px 0px 0px rgba(0, 0, 0, 1);
}

/* Animated Elements */
.typewriter-container {
  transform-origin: center;
}

.cta-primary, .cta-secondary {
  position: relative;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

/* Responsive Adjustments */
@media (max-width: 768px) {
  .hero h1 {
    font-size: 3rem;
  }
  
  .cta-primary, .cta-secondary {
    width: 100%;
    margin-bottom: 1.5rem;
  }

  .shadow-brutal {
    box-shadow: 6px 6px 0px 0px rgba(0, 0, 0, 1);
  }
}

/* Animation Keyframes */
@keyframes slideIn {
  from {
    transform: translateY(50px);
    opacity: 0;
  }
  to {
    transform: translateY(0);
    opacity: 1;
  }
}

@keyframes scaleIn {
  from {
    transform: scale(0.8);
    opacity: 0;
  }
  to {
    transform: scale(1);
    opacity: 1;
  }
}

.hero h1 span { animation: scaleIn 0.8s cubic-bezier(0.4, 0, 0.2, 1) forwards; }
.typewriter-container { animation: slideIn 0.8s cubic-bezier(0.4, 0, 0.2, 1) forwards; }
.cta-primary, .cta-secondary { animation: slideIn 0.8s cubic-bezier(0.4, 0, 0.2, 1) forwards; }

/* Stagger animations */
.hero h1 span:first-child { animation-delay: 0.2s; }
.hero h1 span:last-child { animation-delay: 0.4s; }
.typewriter-container { animation-delay: 0.6s; }
.cta-primary { animation-delay: 0.8s; }
.cta-secondary { animation-delay: 1s; }
</style>