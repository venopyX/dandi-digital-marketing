<template>
  <section id="contact" class="min-h-screen relative overflow-hidden bg-gradient-to-br from-amber-50/90 via-yellow-50/80 to-orange-50/90">
    <!-- Circular Pattern Background -->
    <div class="absolute inset-0 opacity-10">
      <div class="absolute inset-0" style="background-image: url('data:image/svg+xml,%3Csvg width=%2240%22 height=%2240%22 viewBox=%220 0 40 40%22 xmlns=%22http://www.w3.org/2000/svg%22%3E%3Ccircle cx=%2220%22 cy=%2220%22 r=%2218%22 fill=%22none%22 stroke=%22%23FF3366%22 stroke-width=%220.5%22 /%3E%3Ccircle cx=%2220%22 cy=%2220%22 r=%2212%22 fill=%22none%22 stroke=%22%23FFDE59%22 stroke-width=%220.5%22 /%3E%3C/svg%3E'); background-size: 40px 40px;"></div>
      <div class="absolute inset-0 rotate-45" style="background-image: url('data:image/svg+xml,%3Csvg width=%2240%22 height=%2240%22 viewBox=%220 0 40 40%22 xmlns=%22http://www.w3.org/2000/svg%22%3E%3Ccircle cx=%2220%22 cy=%2220%22 r=%2215%22 fill=%22none%22 stroke=%22%234D27F7%22 stroke-width=%220.5%22 /%3E%3C/svg%3E'); background-size: 40px 40px;"></div>
    </div>
    <!-- Glassmorphic Orbs -->
    <div class="absolute inset-0 pointer-events-none overflow-hidden">
      <div class="absolute top-1/4 -right-20 w-[40rem] h-[40rem] bg-gradient-to-br from-amber-300/20 to-yellow-300/20 rounded-full blur-3xl" style="animation: float 15s ease-in-out infinite;"></div>
      <div class="absolute -bottom-32 -left-32 w-[50rem] h-[50rem] bg-gradient-to-tr from-orange-300/20 to-yellow-300/20 rounded-full blur-3xl" style="animation: float-delayed 18s ease-in-out infinite;"></div>
    </div>
    <div class="container mx-auto px-6 py-24 relative z-10">
      <div class="text-center mb-16">
        <h2 class="text-5xl md:text-6xl font-black mb-8 tracking-tight">
          <span class="block bg-gradient-to-r from-amber-500 to-orange-500 bg-clip-text text-transparent">
            Get in Touch
          </span>
        </h2>
        <p class="text-2xl md:text-3xl font-semibold text-gray-700">
          Let's Create Something Amazing
        </p>
      </div>
      <div class="max-w-lg mx-auto space-y-6">
        <!-- Form -->
        <form @submit.prevent="handleSubmit" class="space-y-4">
          <div>
            <label for="name" class="block text-lg font-medium text-gray-700">{{ info.title }}</label>
            <input 
              type="text" 
              id="name" 
              v-model="formData.name" 
              placeholder="Your Name" 
              class="w-full p-3 rounded-lg border border-gray-300 focus:outline-none focus:ring-2 focus:ring-amber-500 transition-all duration-300"
            />
            <span v-if="errors.name" class="text-red-500 text-sm">{{ errors.name }}</span>
          </div>
          <div>
            <label for="email" class="block text-lg font-medium text-gray-700">Email</label>
            <input 
              type="email" 
              id="email" 
              v-model="formData.email" 
              placeholder="Your Email" 
              class="w-full p-3 rounded-lg border border-gray-300 focus:outline-none focus:ring-2 focus:ring-amber-500 transition-all duration-300"
            />
            <span v-if="errors.email" class="text-red-500 text-sm">{{ errors.email }}</span>
          </div>
          <div>
            <label for="message" class="block text-lg font-medium text-gray-700">Message</label>
            <textarea 
              id="message" 
              v-model="formData.message" 
              rows="4" 
              placeholder="Your Message" 
              class="w-full p-3 rounded-lg border border-gray-300 focus:outline-none focus:ring-2 focus:ring-amber-500 transition-all duration-300"
            ></textarea>
            <span v-if="errors.message" class="text-red-500 text-sm">{{ errors.message }}</span>
          </div>
          <button 
            type="submit" 
            class="w-full bg-gradient-to-r from-amber-500 to-orange-500 text-white font-bold py-3 rounded-lg shadow-lg hover:shadow-xl transition-all duration-300"
          >
            {{ isSubmitting ? 'Sending...' : 'Send Message' }}
          </button>
        </form>
        <!-- Success Message -->
        <div v-if="successMessage" class="bg-green-100 border border-green-400 text-green-700 px-4 py-3 rounded-lg">
          {{ successMessage }}
        </div>
        <!-- Follow Us -->
        <div class="text-center mt-8">
          <h3 class="text-2xl font-bold mb-4">Follow Us</h3>
          <div class="flex justify-center gap-4">
            <a 
              v-for="(social, index) in socialLinks" 
              :key="index" 
              :href="social.url" 
              target="_blank" 
              class="text-2xl text-gray-700 hover:text-amber-500 transition-colors duration-300"
            >
              <font-awesome-icon :icon="['fab', social.icon]" />
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';
import { library } from '@fortawesome/fontawesome-svg-core';
import { faInstagram, faLinkedin, faFacebook, faTelegram } from '@fortawesome/free-brands-svg-icons';

// Add icons to the library
library.add(faInstagram, faLinkedin, faFacebook, faTelegram);

export default {
  name: 'ContactSection',
  components: {
    FontAwesomeIcon
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
      successMessage: '',
      info: {
        title: 'Get in Touch',
        details: 'Let\'s Create Something Amazing'
      },
      socialLinks: [
        { name: 'Instagram', icon: 'instagram', url: 'https://www.instagram.com/dandi_digital_marketing_agency' },
        { name: 'LinkedIn', icon: 'linkedin', url: 'https://www.linkedin.com/in/dandi-digital-827b12350' },
        { name: 'Facebook', icon: 'facebook', url: 'https://www.facebook.com/profile.php?id=100082760081622' },
        { name: 'Telegram', icon: 'telegram', url: '#' }
      ]
    };
  },
  methods: {
    async handleSubmit() {
      this.errors = {};
      this.successMessage = '';

      // Basic validation
      if (!this.formData.name) {
        this.errors.name = 'Name is required.';
      }
      if (!this.formData.email) {
        this.errors.email = 'Email is required.';
      } else if (!/\S+@\S+\.\S+/.test(this.formData.email)) {
        this.errors.email = 'Please enter a valid email address.';
      }
      if (!this.formData.message) {
        this.errors.message = 'Message is required.';
      }

      if (Object.keys(this.errors).length > 0) {
        return;
      }

      this.isSubmitting = true;

      try {
        // Simulate API call
        await new Promise(resolve => setTimeout(resolve, 2000));
        this.successMessage = 'Message sent successfully! We\'ll get back to you soon. ✨';
        this.formData = { name: '', email: '', message: '' };
      } catch (error) {
        console.error('Error sending message:', error);
      } finally {
        this.isSubmitting = false;
      }
    }
  }
};
</script>

<style scoped>
@keyframes float {
  0%, 100% { transform: translate(0, 0) rotate(0deg); }
  50% { transform: translate(-20px, 20px) rotate(1deg); }
}
@keyframes float-delayed {
  0%, 100% { transform: translate(0, 0) rotate(0deg); }
  50% { transform: translate(20px, -20px) rotate(-1deg); }
}
</style>