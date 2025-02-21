<template>
  <footer class="footer-section relative min-h-[60vh] bg-gradient-to-br from-[#1a1716] via-[#2b2928]/95 to-[#3a322d]/90 overflow-hidden">
    <!-- Complex Background Pattern -->
    <div class="absolute inset-0 opacity-10">
      <div class="absolute inset-0" style="background-image: radial-gradient(circle at 2px 2px, var(--color-brand-primary) 1px, transparent 0); background-size: 32px 32px;"></div>
      <div class="absolute inset-0 rotate-45" style="background-image: radial-gradient(circle at 2px 2px, var(--color-brand-accent) 1px, transparent 0); background-size: 24px 24px;"></div>
    </div>

    <!-- Glassmorphic Elements -->
    <div class="absolute inset-0 pointer-events-none overflow-hidden">
      <div class="absolute -top-32 -right-32 w-96 h-96 bg-gradient-to-br from-[var(--color-brand-primary)]/10 to-[var(--color-brand-background)]/05 rounded-full blur-3xl"></div>
      <div class="absolute -bottom-40 -left-40 w-[32rem] h-[32rem] bg-gradient-to-tr from-[var(--color-brand-accent)]/10 to-[var(--color-brand-primary)]/05 rounded-full blur-3xl"></div>
    </div>

    <!-- Floating Elements -->
    <div class="absolute inset-0 pointer-events-none" ref="footerEffect">
      <div class="absolute top-20 right-20 w-8 h-8 border-2 border-[var(--color-brand-primary)]/20 rounded-full animate-spin-slow"></div>
      <div class="absolute bottom-32 left-1/4 w-12 h-12 border-2 border-[var(--color-brand-accent)]/20 rounded-lg transform rotate-45 animate-float-slow"></div>
      <div class="absolute top-40 left-20 text-[var(--color-brand-primary)]/20 animate-float">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
          <path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/>
        </svg>
      </div>
    </div>

    <div class="container mx-auto px-6 py-16 relative z-10">
      <div class="grid grid-cols-1 md:grid-cols-4 gap-12">
        <!-- Brand Column -->
        <div class="col-span-1 md:col-span-2">
          <div class="mb-8">
            <h2 class="text-3xl font-black mb-4 text-transparent bg-clip-text bg-gradient-to-r from-[var(--color-brand-primary)] to-[var(--color-brand-accent)]">
              Dandi Digital Marketing
            </h2>
            <p class="text-[var(--color-brand-light)]/70 font-medium">
              Transforming brands with creative digital solutions. Let's create something amazing together.
            </p>
          </div>

          <!-- Newsletter Signup -->
          <div class="newsletter-signup backdrop-blur-md bg-[#1a1716]/50 p-6 rounded-2xl border border-[var(--color-brand-light)]/05 transition-all duration-300 hover:bg-[#1a1716]/60">
            <h3 class="text-[var(--color-brand-light)] font-black mb-4">Stay Updated</h3>
            <form @submit.prevent="handleNewsletter" class="flex gap-2">
              <input 
                type="email" 
                v-model="email"
                placeholder="Enter your email"
                class="flex-grow p-3 bg-[var(--color-brand-background)]/10 rounded-xl border border-[var(--color-brand-light)]/10 text-[var(--color-brand-light)] placeholder:text-[var(--color-brand-light)]/40 focus:bg-[var(--color-brand-background)]/20 transition-all duration-300"
              />
              <button 
                type="submit"
                class="px-6 py-3 bg-gradient-to-r from-[var(--color-brand-primary)] to-[var(--color-brand-accent)] text-[var(--color-brand-light)] font-bold rounded-xl hover:shadow-lg hover:shadow-[var(--color-brand-primary)]/15 transition-all duration-300 flex items-center gap-2"
              >
                <span>Join</span>
                <ArrowRightIcon class="w-5 h-5" />
              </button>
            </form>
          </div>
        </div>

        <!-- Quick Links -->
        <div class="quick-links backdrop-blur-md bg-[#1a1716]/50 p-6 rounded-2xl border border-[var(--color-brand-light)]/05">
          <h3 class="text-xl font-black mb-6 text-transparent bg-clip-text bg-gradient-to-r from-[var(--color-brand-primary)] to-[var(--color-brand-accent)]">
            Quick Links
          </h3>
          <ul class="space-y-4">
            <li v-for="link in quickLinks" :key="link.text">
              <a 
                :href="link.url" 
                class="text-[var(--color-brand-light)]/70 hover:text-[var(--color-brand-primary)] font-medium transition-colors flex items-center gap-2 group"
              >
                <span class="w-2 h-2 bg-gradient-to-r from-[var(--color-brand-primary)] to-[var(--color-brand-accent)] rounded-full group-hover:scale-150 transition-transform"></span>
                {{ link.text }}
              </a>
            </li>
          </ul>
        </div>

        <!-- Services -->
        <div class="services backdrop-blur-md bg-[#1a1716]/50 p-6 rounded-2xl border border-[var(--color-brand-light)]/05">
          <h3 class="text-xl font-black mb-6 text-transparent bg-clip-text bg-gradient-to-r from-[var(--color-brand-primary)] to-[var(--color-brand-accent)]">
            Services
          </h3>
          <ul class="space-y-4">
            <li v-for="service in services" :key="service">
              <span class="text-[var(--color-brand-light)]/70 font-medium flex items-center gap-2">
                <span class="w-2 h-2 bg-gradient-to-r from-[var(--color-brand-primary)] to-[var(--color-brand-accent)] rounded-full"></span>
                {{ service }}
              </span>
            </li>
          </ul>
        </div>
      </div>

      <!-- Bottom Bar -->
      <div class="mt-16 pt-8 border-t border-[var(--color-brand-light)]/05">
        <div class="flex flex-col md:flex-row justify-between items-center gap-4">
          <p class="text-[var(--color-brand-light)]/70 font-medium">
            © {{ new Date().getFullYear() }} Dandi Digital Marketing. All rights reserved.
          </p>
          <div class="flex gap-8">
            <a 
              v-for="link in legalLinks" 
              :key="link.text"
              :href="link.url"
              class="text-[var(--color-brand-light)]/70 hover:text-[var(--color-brand-primary)] font-medium transition-colors"
            >
              {{ link.text }}
            </a>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
import { ArrowRightIcon } from '@heroicons/vue/24/outline'

export default {
  name: 'FooterSection',
  components: {
    ArrowRightIcon
  },
  data() {
    return {
      email: '',
      quickLinks: [
        { text: 'Home', url: '#' },
        { text: 'About Us', url: '#about' },
        { text: 'Services', url: '#services' },
        { text: 'Portfolio', url: '#portfolio' },
        { text: 'Contact', url: '#contact' }
      ],
      services: [
        'Brand Strategy',
        'Digital Marketing',
        'Social Media Management',
        'Content Creation',
        'Web Development'
      ],
      legalLinks: [
        { text: 'Privacy Policy', url: '#' },
        { text: 'Terms of Service', url: '#' },
        { text: 'Cookie Policy', url: '#' }
      ]
    }
  },
  methods: {
    handleNewsletter() {
      console.log('Newsletter signup:', this.email)
      this.email = ''
    },
    initParallaxEffect() {
      document.addEventListener("mousemove", (e) => {
        const footer = this.$refs.footerEffect;
        if (footer) {
          const x = (e.clientX / window.innerWidth - 0.5) * 10;
          const y = (e.clientY / window.innerHeight - 0.5) * 10;
          footer.style.transform = `translate(${x}px, ${y}px)`;
        }
      });
    }
  },
  mounted() {
    this.initParallaxEffect();
  }
}
</script>

<style scoped>
@keyframes spin-slow {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

@keyframes float-slow {
  0%, 100% { transform: translateY(0) rotate(45deg); }
  50% { transform: translateY(-15px) rotate(60deg); }
}

@keyframes float {
  0%, 100% { transform: translateY(0) rotate(0); }
  50% { transform: translateY(-10px) rotate(5deg); }
}

.animate-spin-slow {
  animation: spin-slow 8s linear infinite;
}

.animate-float-slow {
  animation: float-slow 6s ease-in-out infinite;
}

.animate-float {
  animation: float 3s ease-in-out infinite;
}
</style>