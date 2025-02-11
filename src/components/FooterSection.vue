<template>
  <footer class="footer-section bg-black text-white py-16 relative">
    <!-- Decorative Elements -->
    <div class="absolute inset-0 overflow-hidden">
      <div class="absolute -right-12 top-12 w-64 h-64 bg-[#FFDE59] border-[6px] border-white transform rotate-12 opacity-10"></div>
      <div class="absolute -left-12 bottom-12 w-48 h-48 bg-[#FF3366] border-[6px] border-white transform -rotate-12 opacity-10"></div>
    </div>

    <div class="container mx-auto px-6 relative">
      <div class="grid grid-cols-1 md:grid-cols-4 gap-12">
        <!-- Brand Column -->
        <div class="col-span-1 md:col-span-2">
          <div class="mb-8">
            <h2 class="text-3xl font-black mb-4 bg-[#4D27F7] px-4 py-2 inline-block transform -rotate-2 border-[4px] border-white">
              Dandi Digital Marketing
            </h2>
            <p class="text-gray-300 font-medium">
              Transforming brands with creative digital solutions. Let's create something amazing together.
            </p>
          </div>

          <!-- Newsletter Signup -->
          <div class="newsletter-signup bg-white p-6 border-[6px] border-black shadow-brutal transform hover:-translate-y-1 hover:translate-x-1 transition-transform">
            <h3 class="text-black font-black mb-4">Stay Updated</h3>
            <form @submit.prevent="handleNewsletter" class="flex gap-2">
              <input 
                type="email" 
                v-model="email"
                placeholder="Enter your email"
                class="flex-grow p-3 border-[4px] border-black focus:bg-[#FFDE59] focus:-translate-y-1 focus:translate-x-1 transition-all font-medium"
              />
              <button 
                type="submit"
                class="px-6 py-3 bg-[#FF3366] text-white font-bold border-[4px] border-black hover:bg-[#4D27F7] transition-colors shadow-brutal flex items-center gap-2"
              >
                <span>Join</span>
                <ArrowRightIcon class="w-5 h-5" />
              </button>
            </form>
          </div>
        </div>

        <!-- Quick Links -->
        <div class="quick-links">
          <h3 class="text-xl font-black mb-6 bg-[#00C6BE] px-4 py-2 inline-block transform rotate-1 border-[4px] border-white">
            Quick Links
          </h3>
          <ul class="space-y-4">
            <li v-for="link in quickLinks" :key="link.text">
              <a 
                :href="link.url" 
                class="text-gray-300 hover:text-[#FFDE59] font-medium transition-colors flex items-center gap-2 group"
              >
                <span class="w-2 h-2 bg-[#FFDE59] group-hover:bg-white transition-colors"></span>
                {{ link.text }}
              </a>
            </li>
          </ul>
        </div>

        <!-- Services -->
        <div class="services">
          <h3 class="text-xl font-black mb-6 bg-[#FF3366] px-4 py-2 inline-block transform -rotate-1 border-[4px] border-white">
            Services
          </h3>
          <ul class="space-y-4">
            <li v-for="service in services" :key="service">
              <span class="text-gray-300 font-medium flex items-center gap-2">
                <span class="w-2 h-2 bg-[#FF3366]"></span>
                {{ service }}
              </span>
            </li>
          </ul>
        </div>
      </div>

      <!-- Bottom Bar -->
      <div class="mt-16 pt-8 border-t-[4px] border-white">
        <div class="flex flex-col md:flex-row justify-between items-center gap-4">
          <p class="text-gray-300 font-medium">
            © {{ new Date().getFullYear() }} Dandi Digital Marketing. All rights reserved.
          </p>
          <div class="flex gap-8">
            <a 
              v-for="link in legalLinks" 
              :key="link.text"
              :href="link.url"
              class="text-gray-300 hover:text-[#FFDE59] font-medium transition-colors"
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
      // Handle newsletter signup
      console.log('Newsletter signup:', this.email)
      this.email = ''
    }
  }
}
</script>

<style scoped>
.shadow-brutal {
  box-shadow: 6px 6px 0 rgba(0, 0, 0, 1);
}

/* Responsive Adjustments */
@media (max-width: 768px) {
  .shadow-brutal {
    box-shadow: 4px 4px 0 rgba(0, 0, 0, 1);
  }

  .newsletter-signup {
    transform: none !important;
  }

  .newsletter-signup input:focus,
  .newsletter-signup button:hover {
    transform: none !important;
  }
}
</style>
