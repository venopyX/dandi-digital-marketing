<template>
  <section id="contact" class="relative min-h-screen py-24 bg-gradient-to-br from-teal-50/90 via-cyan-50/80 to-blue-50/90 overflow-hidden">
    <!-- Complex Background Pattern -->
    <div class="absolute inset-0 opacity-10">
      <div class="absolute inset-0" style="background-image: radial-gradient(circle at 2px 2px, #00C6BE 1px, transparent 0); background-size: 32px 32px;"></div>
      <div class="absolute inset-0 rotate-45" style="background-image: radial-gradient(circle at 2px 2px, #4D27F7 1px, transparent 0); background-size: 24px 24px;"></div>
    </div>

    <!-- Large Circular Glassmorphic Elements -->
    <div class="absolute inset-0 pointer-events-none overflow-hidden">
      <div class="absolute -top-32 -right-32 w-96 h-96 bg-gradient-to-br from-teal-300/20 to-blue-300/20 rounded-full blur-3xl"></div>
      <div class="absolute -bottom-40 -left-40 w-[32rem] h-[32rem] bg-gradient-to-tr from-cyan-300/20 to-teal-300/20 rounded-full blur-3xl"></div>
    </div>

    <!-- Enhanced Floating Elements -->
    <div class="absolute inset-0 pointer-events-none" ref="backgroundEffect">
      <!-- Decorative Elements -->
      <div class="absolute top-20 right-20 text-teal-300/80 animate-float">
        <EnvelopeIcon class="w-8 h-8" />
      </div>
      <div class="absolute bottom-32 left-1/4 text-cyan-300/60 animate-float-delay">
        <PhoneIcon class="w-6 h-6" />
      </div>
      <div class="absolute top-40 left-20 text-blue-400/80 animate-twinkle">
        <MapPinIcon class="w-8 h-8" />
      </div>
      
      <!-- Geometric Shapes -->
      <div class="absolute top-1/4 left-1/3 w-8 h-8 border-2 border-teal-300/30 rounded-full animate-spin-slow"></div>
      <div class="absolute bottom-1/3 right-1/4 w-12 h-12 border-2 border-cyan-300/30 rounded-lg transform rotate-45 animate-float-slow"></div>
    </div>

    <div class="container mx-auto px-6 relative z-10">
      <!-- Section Header -->
      <div class="text-center mb-16">
        <div class="inline-block bg-white/80 backdrop-blur-sm rounded-full px-6 py-2 mb-6 shadow-lg transform -rotate-1 border border-teal-200">
          <span class="text-lg font-bold bg-gradient-to-r from-teal-500 to-blue-500 bg-clip-text text-transparent">
            Get in Touch
          </span>
        </div>
        <h2 class="text-5xl md:text-6xl font-black mb-6 tracking-tight">
          <span class="block bg-gradient-to-r from-teal-500 to-blue-500 bg-clip-text text-transparent">
            Let's Create
          </span>
          <span class="block text-teal-400 mt-2">
            Something Amazing
          </span>
        </h2>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-2 gap-16">
        <!-- Contact Information -->
        <div class="space-y-8">
          <div v-for="(info, index) in contactInfo" 
               :key="index"
               class="bg-white/80 backdrop-blur-sm rounded-2xl p-6 shadow-lg transform hover:-translate-y-1 transition-all duration-300">
            <div class="flex items-center space-x-4">
              <div class="p-4 rounded-xl bg-gradient-to-r from-teal-500 to-blue-500 text-white">
                <component :is="info.icon" class="w-6 h-6" />
              </div>
              <div>
                <h3 class="text-xl font-bold text-gray-800">{{ info.title }}</h3>
                <p class="text-gray-600">{{ info.details }}</p>
              </div>
            </div>
          </div>

          <!-- Social Links -->
          <div class="bg-white/80 backdrop-blur-sm rounded-2xl p-6 shadow-lg">
            <h3 class="text-xl font-bold mb-4 bg-gradient-to-r from-teal-500 to-blue-500 bg-clip-text text-transparent">Follow Us</h3>
            <div class="flex space-x-4">
              <a v-for="social in socialLinks" 
                 :key="social.name"
                 :href="social.url"
                 class="p-3 rounded-xl bg-gradient-to-r from-teal-500/10 to-blue-500/10 hover:from-teal-500 hover:to-blue-500 hover:text-white transition-all duration-300">
                <component :is="social.icon" class="w-5 h-5" />
              </a>
            </div>
          </div>
        </div>

        <!-- Contact Form -->
        <div class="bg-white/80 backdrop-blur-sm rounded-2xl p-8 shadow-lg">
          <form @submit.prevent="handleSubmit" class="space-y-6">
            <div v-for="(field, key) in formFields" :key="key" class="space-y-2">
              <label class="block text-gray-700 font-bold">{{ field.label }}</label>
              <component
                :is="field.type === 'textarea' ? 'textarea' : 'input'"
                v-model="formData[key]"
                :type="field.type"
                :class="[
                  'w-full px-4 py-3 rounded-xl border border-gray-200',
                  'focus:ring-2 focus:ring-teal-500 focus:border-transparent',
                  'backdrop-blur-sm transition-all duration-300',
                  field.type === 'textarea' ? 'min-h-[150px]' : '',
                  errors[key] ? 'border-red-300' : ''
                ]"
                @focus="clearError(key)"
              />
              <span v-if="errors[key]" class="text-red-500 text-sm">{{ errors[key] }}</span>
            </div>

            <button
              type="submit"
              :disabled="isSubmitting"
              class="w-full py-4 px-6 rounded-xl font-bold text-white shadow-lg
                     bg-gradient-to-r from-teal-500 to-blue-500 
                     hover:from-teal-600 hover:to-blue-600
                     transform hover:-translate-y-1 transition-all duration-300
                     disabled:opacity-50 disabled:cursor-not-allowed
                     flex items-center justify-center space-x-2"
            >
              <ArrowPathIcon v-if="isSubmitting" class="animate-spin w-5 h-5" />
              <span>{{ isSubmitting ? 'Sending...' : 'Send Message' }}</span>
            </button>
          </form>

          <!-- Success Message -->
          <div v-if="showSuccess"
               class="mt-6 p-4 rounded-xl bg-gradient-to-r from-teal-500 to-blue-500 text-white
                      transform animate-slideIn">
            Message sent successfully! We'll get back to you soon. ✨
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import {
  EnvelopeIcon,
  PhoneIcon,
  MapPinIcon,
  UserGroupIcon,
  HashtagIcon,
  GlobeAltIcon,
  ArrowPathIcon
} from '@heroicons/vue/24/outline'

export default {
  name: 'ContactSection',
  components: {
    EnvelopeIcon,
    PhoneIcon,
    MapPinIcon,
    UserGroupIcon,
    HashtagIcon,
    GlobeAltIcon,
    ArrowPathIcon
  },
  data() {
    return {
      formData: {
        name: '',
        email: '',
        message: ''
      },
      formFields: {
        name: { label: 'Your Name', type: 'text' },
        email: { label: 'Your Email', type: 'email' },
        message: { label: 'Your Message', type: 'textarea' }
      },
      errors: {},
      isSubmitting: false,
      showSuccess: false,
      contactInfo: [
        {
          icon: 'EnvelopeIcon',
          title: 'Email',
          details: 'hello@dandidigital.com'
        },
        {
          icon: 'PhoneIcon',
          title: 'Phone',
          details: '+1 (234) 567-8900'
        },
        {
          icon: 'MapPinIcon',
          title: 'Location',
          details: 'Melbourne, Australia'
        }
      ],
      socialLinks: [
        { name: 'Community', icon: 'UserGroupIcon', url: '#' },
        { name: 'Social', icon: 'HashtagIcon', url: '#' },
        { name: 'Website', icon: 'GlobeAltIcon', url: '#' }
      ]
    }
  },
  mounted() {
    this.initParallaxEffect();
  },
  methods: {
    initParallaxEffect() {
      document.addEventListener("mousemove", (e) => {
        const bg = this.$refs.backgroundEffect;
        if (bg) {
          const x = (e.clientX / window.innerWidth - 0.5) * 10;
          const y = (e.clientY / window.innerHeight - 0.5) * 10;
          bg.style.transform = `translate(${x}px, ${y}px)`;
        }
      });
    },
    validateForm() {
      this.errors = {};
      if (!this.formData.name) this.errors.name = 'Name is required';
      if (!this.formData.email) {
        this.errors.email = 'Email is required';
      } else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(this.formData.email)) {
        this.errors.email = 'Please enter a valid email';
      }
      if (!this.formData.message) this.errors.message = 'Message is required';
      return Object.keys(this.errors).length === 0;
    },
    clearError(field) {
      this.$delete(this.errors, field);
    },
    async handleSubmit() {
      if (!this.validateForm()) return;
      
      this.isSubmitting = true;
      await new Promise(resolve => setTimeout(resolve, 1500));
      
      this.isSubmitting = false;
      this.showSuccess = true;
      this.formData = { name: '', email: '', message: '' };
      
      setTimeout(() => {
        this.showSuccess = false;
      }, 5000);
    }
  }
}
</script>

<style scoped>
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

.animate-spin-slow {
  animation: spin-slow 8s linear infinite;
}

.animate-float-slow {
  animation: float-slow 6s ease-in-out infinite;
}

@keyframes slideIn {
  from {
    opacity: 0;
    transform: translateY(-20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-slideIn {
  animation: slideIn 0.3s ease-out;
}
</style>