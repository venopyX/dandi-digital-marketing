<template>
  <nav class="fixed w-full top-0 z-50 transition-all duration-300">
    <!-- Backdrop Blur Container -->
    <div class="absolute inset-0 bg-[var(--color-brand-light)]/70 backdrop-blur-lg shadow-lg"></div>
    
    <!-- Main Navigation Content -->
    <div class="container mx-auto px-6 relative">
      <div class="flex justify-between items-center h-20">
        <!-- Logo Area -->
        <div class="relative">
          <a href="/" class="flex items-center gap-3 group">
            <div class="w-10 h-10 bg-gradient-to-br from-[var(--color-brand-light)] to-[var(--color-brand-accent)]/20 rounded-lg flex items-center justify-center text-white font-black text-xl shadow-lg">
              <img src="../assets/logo.png" alt="Logo" class="w-10 h-10 object-cover object-center">
            </div>
            <span class="text-xl font-bold bg-gradient-to-r from-[var(--color-brand-primary)] to-[var(--color-brand-accent)] bg-clip-text text-transparent group-hover:opacity-80 transition-opacity">
              Dandi Digital Marketing
            </span>
          </a>
        </div>

        <!-- Desktop Menu -->
        <div class="hidden md:flex items-center gap-6">
          <template v-for="(item, index) in menuItems" :key="index">
            <a
              :href="item.href"
              class="relative px-4 py-2 font-medium text-[var(--color-brand-secondary)] hover:text-[var(--color-brand-primary)] transition-colors flex items-center gap-2 group"
              :class="{ 'text-[var(--color-brand-primary)]': item.active }"
            >
              <component 
                :is="item.icon" 
                class="w-5 h-5 transition-transform group-hover:scale-110" 
              />
              <span>{{ item.label }}</span>
              <!-- Hover Effect -->
              <div class="absolute inset-0 bg-[var(--color-brand-light)]/30 rounded-xl scale-0 group-hover:scale-100 transition-transform"></div>
              <!-- Active Indicator -->
              <div 
                v-if="item.active" 
                class="absolute -bottom-1 left-0 right-0 h-0.5 bg-gradient-to-r from-[var(--color-brand-primary)] to-[var(--color-brand-accent)]"
              ></div>
            </a>
          </template>
        </div>

        <!-- Contact Button (Desktop) -->
        <div class="hidden md:block">
        <button class="px-6 py-2.5 bg-gradient-to-r from-[var(--color-brand-primary)] to-[var(--color-brand-accent)] text-white font-medium rounded-xl shadow-lg hover:shadow-xl transition-all duration-300 hover:-translate-y-0.5 flex items-center gap-2" onclick="window.open('https://www.linkedin.com/in/dandi-digital-827b12350', '_blank')">
            <EnvelopeIcon class="w-5 h-5" />
            Contact Us
          </button>
        </div>

        <!-- Mobile Menu Toggle -->
        <button
          @click="toggleMobileMenu"
          class="md:hidden relative z-50 p-2 rounded-xl bg-[var(--color-brand-light)]/80 backdrop-blur-sm hover:bg-[var(--color-brand-light)]/50 transition-colors"
          :class="{ 'bg-[var(--color-brand-light)]/50': isMobileMenuOpen }"
        >
          <div class="w-6 h-5 flex flex-col justify-between">
            <span class="block w-full h-0.5 bg-[var(--color-brand-secondary)] transition-transform" :class="{ 'rotate-45 translate-y-2': isMobileMenuOpen }"></span>
            <span class="block w-full h-0.5 bg-[var(--color-brand-secondary)] transition-opacity" :class="{ 'opacity-0': isMobileMenuOpen }"></span>
            <span class="block w-full h-0.5 bg-[var(--color-brand-secondary)] transition-transform" :class="{ '-rotate-45 -translate-y-2': isMobileMenuOpen }"></span>
          </div>
        </button>
      </div>
    </div>

    <!-- Mobile Menu Panel -->
    <div
      v-show="isMobileMenuOpen"
      class="md:hidden absolute inset-x-0 top-0 pt-20 bg-[var(--color-brand-light)]/90 backdrop-blur-lg shadow-lg"
    >
      <div class="container mx-auto px-6">
        <div class="py-6 space-y-4">
          <template v-for="(item, index) in menuItems" :key="index">
            <a
              :href="item.href"
              @click="closeMobileMenu"
              class="relative flex items-center gap-3 px-4 py-3 rounded-xl font-medium text-[var(--color-brand-secondary)] hover:text-[var(--color-brand-primary)] hover:bg-[var(--color-brand-light)]/50 transition-colors group"
              :class="{ 'bg-[var(--color-brand-light)]/30 text-[var(--color-brand-primary)]': item.active }"
            >
              <component :is="item.icon" class="w-5 h-5" />
              <span>{{ item.label }}</span>
              <!-- Hover Effect -->
              <div class="absolute inset-0 bg-[var(--color-brand-light)]/50 rounded-xl scale-0 group-hover:scale-100 transition-transform"></div>
            </a>
          </template>
          <div class="pt-4 border-t border-[var(--color-brand-light)]/50">
            <button 
              @click="closeMobileMenu" 
              class="w-full py-3 bg-gradient-to-r from-[var(--color-brand-primary)] to-[var(--color-brand-accent)] text-white font-medium rounded-xl shadow-lg hover:shadow-xl transition-all duration-300 flex items-center justify-center gap-2"
            >
              <EnvelopeIcon class="w-5 h-5" />
              Contact Us
            </button>
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
import {
  HomeIcon,
  WrenchScrewdriverIcon,
  RectangleStackIcon,
  UserGroupIcon,
  EnvelopeIcon,
  Bars3Icon,
  XMarkIcon
} from '@heroicons/vue/24/outline'

export default {
  name: 'NavBar',
  components: {
    HomeIcon,
    WrenchScrewdriverIcon,
    RectangleStackIcon,
    UserGroupIcon,
    EnvelopeIcon,
    Bars3Icon,
    XMarkIcon
  },
  data() {
    return {
      isMobileMenuOpen: false,
      menuItems: [
        { label: 'Home', href: '#', icon: 'HomeIcon', active: false },
        { label: 'Services', href: '#services', icon: 'WrenchScrewdriverIcon', active: false },
        { label: 'Portfolio', href: '#portfolio', icon: 'RectangleStackIcon', active: false },
        { label: 'About', href: '#about', icon: 'UserGroupIcon', active: false },
        { label: 'Contact', href: '#contact', icon: 'EnvelopeIcon', active: false }
      ]
    }
  },
  methods: {
    toggleMobileMenu() {
      this.isMobileMenuOpen = !this.isMobileMenuOpen;
    },
    closeMobileMenu() {
      this.isMobileMenuOpen = false;
    },
    handleScroll() {
      const scrollPosition = window.scrollY;
      if (scrollPosition > 50) {
        this.$el.classList.add('nav-scrolled');
      } else {
        this.$el.classList.remove('nav-scrolled');
      }
    }
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.handleScroll);
  }
}
</script>

<style scoped>
.nav-scrolled {
  @supports (backdrop-filter: blur(12px)) {
    background-color: rgba(var(--color-brand-light-rgb), 0.7);
    backdrop-filter: blur(12px);
  }
  
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 
              0 2px 4px -1px rgba(0, 0, 0, 0.06);
}

/* Mobile Menu Animation */
.mobile-menu {
  animation: slideIn 0.3s ease-out forwards;
}

@keyframes slideIn {
  from {
    opacity: 0;
    transform: translateY(-1rem);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Ensure smooth transitions */
* {
  transition-property: transform, opacity, background-color, box-shadow;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
  transition-duration: 300ms;
}
</style>