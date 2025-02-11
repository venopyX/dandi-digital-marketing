<template>
  <nav class="nav-container fixed w-full top-0 z-50 bg-[#FFDE59]">
    <!-- Desktop Navigation -->
    <div class="container mx-auto px-6">
      <div class="nav-content flex justify-between items-center h-20 border-b-[6px] border-black">
        <!-- Logo Area -->
        <div class="nav-logo">
          <a href="/" class="text-3xl font-black tracking-tight hover:rotate-2 transition-transform inline-block">
            Dandi Digital Marketing
          </a>
        </div>

        <!-- Desktop Menu -->
        <div class="hidden md:flex space-x-8">
          <template v-for="(item, index) in menuItems" :key="index">
            <a
              :href="item.href"
              class="nav-link relative font-bold text-lg px-4 py-2 hover:-rotate-3 hover:scale-110 transition-transform inline-block flex items-center gap-2"
              :class="{ 'active': item.active }"
            >
              <component :is="item.icon" class="w-5 h-5" />
              {{ item.label }}
            </a>
          </template>
        </div>

        <!-- Contact Button (Desktop) -->
        <div class="hidden md:block">
          <button class="contact-btn px-6 py-2 bg-[#FF3366] text-white font-bold border-[6px] border-black hover:translate-x-1 hover:-translate-y-1 transition-transform shadow-brutal flex items-center gap-2">
            <EnvelopeIcon class="w-5 h-5" />
            Contact Us
          </button>
        </div>

        <!-- Mobile Menu Toggle -->
        <button
          @click="toggleMobileMenu"
          class="md:hidden mobile-toggle p-2 border-4 border-black hover:bg-gray-100"
          :class="{ 'active': isMobileMenuOpen }"
        >
          <div class="w-6 h-5 relative flex flex-col justify-between">
            <span class="block w-full h-1 bg-black transition-transform"></span>
            <span class="block w-full h-1 bg-black transition-opacity"></span>
            <span class="block w-full h-1 bg-black transition-transform"></span>
          </div>
        </button>
      </div>
    </div>

    <!-- Mobile Menu Panel -->
    <div
      v-show="isMobileMenuOpen"
      class="mobile-menu md:hidden"
    >
      <div class="container mx-auto px-6">
        <div class="py-4 space-y-4 border-x-4 border-b-4 border-black bg-white">
          <template v-for="(item, index) in menuItems" :key="index">
            <a
              :href="item.href"
              class="block px-4 py-3 font-bold text-lg hover:bg-gray-100 transition-colors flex items-center gap-2"
              :class="{ 'active': item.active }"
            >
              <component :is="item.icon" class="w-5 h-5" />
              {{ item.label }}
            </a>
          </template>
          <div class="px-4 pt-4 border-t-4 border-black">
            <button class="w-full py-3 bg-black text-white font-bold border-4 border-black hover:bg-[#FF3366] hover:border-[#FF3366] transition-colors flex items-center justify-center gap-2">
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
    handleScroll() {
      // Add scroll handling logic here
      const scrollPosition = window.scrollY;
      if (scrollPosition > 50) {
        // Add shadow class when scrolled
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
/* Neo-Brutalist Navigation Styles */
.nav-container {
  transition: transform 0.3s ease;
}

.nav-scrolled {
  box-shadow: 8px 8px 0 rgba(0, 0, 0, 1);
}

/* Desktop Navigation Link Styles */
.nav-link {
  transition: transform 0.3s ease;
  background-color: white;
  border: 4px solid black;
  box-shadow: 4px 4px 0 rgba(0, 0, 0, 1);
}

/* Mobile Toggle Button */
.mobile-toggle {
  background-color: white;
}

.mobile-toggle span {
  transform-origin: center;
  transition: all 0.3s ease;
}

.mobile-toggle.active span:first-child {
  transform: translateY(8px) rotate(45deg);
}

.mobile-toggle.active span:nth-child(2) {
  opacity: 0;
}

.mobile-toggle.active span:last-child {
  transform: translateY(-8px) rotate(-45deg);
}

/* Mobile Menu Animation */
.mobile-menu {
  animation: slideDown 0.3s ease-out forwards;
}

@keyframes slideDown {
  from {
    opacity: 0;
    transform: translateY(-10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Contact Button Hover Effect */
.contact-btn {
  transition: transform 0.3s ease;
}

/* Shadow Utility Class */
.shadow-brutal {
  box-shadow: 8px 8px 0 rgba(0, 0, 0, 1);
}

/* Active State Styles */
.nav-link.active {
  background-color: #FF3366;
  color: white;
}

/* Responsive Adjustments */
@media (max-width: 768px) {
  .nav-container {
    border-bottom: 6px solid black;
  }
}
</style>
