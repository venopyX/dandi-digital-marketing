<template>
  <section id="contact" class="contact-section py-24 relative bg-[#00C6BE]">
    <!-- Decorative Background -->
    <div class="absolute inset-0 bg-pattern opacity-10"></div>
    
    <div class="container mx-auto px-6">
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-16">
        <!-- Contact Information -->
        <div class="contact-info">
          <span class="inline-block px-6 py-3 bg-black text-white font-mono mb-4 transform -rotate-2 border-[6px] border-black shadow-brutal">
            Get in Touch
          </span>
          <h2 class="text-5xl md:text-6xl font-black mb-8 relative inline-block bg-white px-6 py-3 border-[6px] border-black shadow-brutal transform rotate-1">Let's Create Something Amazing</h2>
          
          <div class="space-y-8">
            <!-- Contact Cards -->
            <div 
              v-for="(info, index) in contactInfo" 
              :key="index"
              class="contact-card bg-white p-6 border-[6px] border-black shadow-brutal transform hover:-translate-y-2 hover:translate-x-2 transition-transform mb-6"
            >
              <div class="flex items-start space-x-4">
                <div class="icon-wrapper bg-[#FFDE59] p-4 border-[4px] border-black">
                  <component 
                    :is="info.icon" 
                    class="w-6 h-6"
                  />
                </div>
                <div>
                  <h3 class="text-xl font-black mb-2">{{ info.title }}</h3>
                  <p class="text-gray-800 font-medium">{{ info.details }}</p>
                </div>
              </div>
            </div>

            <!-- Social Links -->
            <div class="social-links mt-12 bg-white p-6 border-[6px] border-black shadow-brutal transform hover:-translate-y-2 hover:translate-x-2 transition-transform">
              <h3 class="text-xl font-black mb-4 px-4 py-2 bg-[#4D27F7] text-white inline-block transform -rotate-1 border-[4px] border-black">Follow Us</h3>
              <div class="flex space-x-4">
                <a 
                  v-for="(social, index) in socialLinks" 
                  :key="index"
                  :href="social.url"
                  class="social-icon p-4 bg-[#FFDE59] border-[4px] border-black hover:bg-[#FF3366] hover:text-white transition-colors transform hover:-rotate-2"
                  :title="social.name"
                >
                  <component 
                    :is="social.icon" 
                    class="w-5 h-5"
                  />
                </a>
              </div>
            </div>
          </div>
        </div>

        <!-- Contact Form -->
        <div class="contact-form-wrapper bg-white p-8 border-[6px] border-black shadow-brutal">
          <form @submit.prevent="handleSubmit" class="contact-form space-y-6">
            <!-- Name Input -->
            <div class="form-group">
              <label class="form-label font-black text-lg">Your Name</label>
              <input 
                v-model="formData.name"
                type="text"
                class="form-input bg-white border-[4px] border-black p-4 w-full font-medium focus:bg-[#FFDE59] focus:-translate-y-1 focus:translate-x-1 transition-all"
                :class="{ 'error border-[#FF3366]': errors.name }"
                @focus="clearError('name')"
              />
              <span v-if="errors.name" class="error-message text-[#FF3366] font-bold">{{ errors.name }}</span>
            </div>

            <!-- Email Input -->
            <div class="form-group">
              <label class="form-label font-black text-lg">Your Email</label>
              <input 
                v-model="formData.email"
                type="email"
                class="form-input bg-white border-[4px] border-black p-4 w-full font-medium focus:bg-[#FFDE59] focus:-translate-y-1 focus:translate-x-1 transition-all"
                :class="{ 'error border-[#FF3366]': errors.email }"
                @focus="clearError('email')"
              />
              <span v-if="errors.email" class="error-message text-[#FF3366] font-bold">{{ errors.email }}</span>
            </div>

            <!-- Message Input -->
            <div class="form-group">
              <label class="form-label font-black text-lg">Your Message</label>
              <textarea 
                v-model="formData.message"
                class="form-input bg-white border-[4px] border-black p-4 w-full font-medium focus:bg-[#FFDE59] focus:-translate-y-1 focus:translate-x-1 transition-all min-h-[150px]"
                :class="{ 'error border-[#FF3366]': errors.message }"
                @focus="clearError('message')"
              ></textarea>
              <span v-if="errors.message" class="error-message text-[#FF3366] font-bold">{{ errors.message }}</span>
            </div>

            <!-- Submit Button -->
            <button 
              type="submit"
              class="submit-button w-full py-4 px-8 bg-[#4D27F7] text-white font-black border-[6px] border-black shadow-brutal hover:-translate-y-1 hover:translate-x-1 transition-all disabled:opacity-50 disabled:cursor-not-allowed"
              :disabled="isSubmitting"
            >
              <span v-if="!isSubmitting">Send Message →</span>
              <span v-else class="flex items-center justify-center">
                <component 
                  :is="'ArrowPathIcon'"
                  class="animate-spin mr-2 w-5 h-5"
                />
                Sending...
              </span>
            </button>
          </form>

          <!-- Success Message -->
          <div 
            v-if="showSuccess"
            class="success-message mt-6 p-4 bg-[#00C6BE] text-white font-bold border-[4px] border-black shadow-brutal animate-slideIn"
          >
            Message sent successfully! We'll get back to you soon. 🎉
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
  methods: {
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
      
      // Simulate API call
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
.bg-pattern {
  background-image: radial-gradient(#000 2px, transparent 2px);
  background-size: 48px 48px;
}

.shadow-brutal {
  box-shadow: 8px 8px 0 rgba(0, 0, 0, 1);
}

.form-group {
  position: relative;
  margin-bottom: 2rem;
}

.error-message {
  position: absolute;
  bottom: -1.5rem;
  left: 0;
  font-size: 0.875rem;
}

@keyframes shake {
  0%, 100% { transform: translateX(0); }
  25% { transform: translateX(-8px); }
  75% { transform: translateX(8px); }
}

.animate-slideIn {
  animation: slideIn 0.3s ease-out;
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

/* Responsive Adjustments */
@media (max-width: 768px) {
  .shadow-brutal {
    box-shadow: 6px 6px 0 rgba(0, 0, 0, 1);
  }

  .contact-card,
  .social-links,
  .contact-form-wrapper {
    transform: none !important;
  }

  .form-input:focus,
  .submit-button:hover {
    transform: none !important;
  }
}
</style>