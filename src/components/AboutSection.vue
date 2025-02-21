<template>
  <section id="about" class="min-h-screen relative overflow-hidden bg-gradient-to-br from-amber-50/90 via-yellow-50/80 to-orange-50/90">
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
      <!-- Section Header -->
      <div class="text-center mb-16">
        <div class="inline-block bg-white/70 backdrop-blur-sm rounded-full px-6 py-2 mb-6 shadow-lg transform hover:scale-105 transition-all duration-300">
          <span class="text-lg font-bold bg-gradient-to-r from-amber-500 to-orange-500 bg-clip-text text-transparent">
            About Us
          </span>
        </div>
        <h2 class="text-5xl md:text-6xl font-black mb-8 tracking-tight">
          <span class="block bg-gradient-to-r from-amber-500 to-orange-500 bg-clip-text text-transparent">
            Meet Dandi
          </span>
        </h2>
      </div>
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12">
        <!-- Biography Column -->
        <div class="relative group">
          <!-- Card Background -->
          <div class="absolute inset-0 bg-gradient-to-br from-white/50 to-white/30 backdrop-blur-md rounded-2xl border border-white/20 shadow-lg transition-all duration-300 group-hover:scale-[1.01] group-hover:shadow-xl"></div>
          
          <div class="relative p-8">
            <!-- Profile Image -->
            <div class="mb-8 lg:float-right lg:ml-8 lg:mb-4">
              <div class="relative">
                <!-- Portrait-friendly container -->
                <div class="w-48 h-64 md:w-64 md:h-96 overflow-hidden rounded-2xl bg-gradient-to-br from-white/80 to-white/50 backdrop-blur-sm p-2 shadow-lg transition-transform duration-300 group-hover:scale-105">
                  <img 
                    src="../assets/dandi-kitessa.webp" 
                    alt="Dandi Kitessa"
                    class="w-full h-full object-cover rounded-xl transition-transform duration-500 group-hover:scale-110"
                  />
                </div>
                <div class="absolute -z-10 inset-0 bg-gradient-to-r from-amber-500 to-orange-500 rounded-2xl blur-xl opacity-20 transition-opacity duration-300 group-hover:opacity-30"></div>
              </div>
            </div>
            <!-- Biography Text -->
            <div class="space-y-6">
              <div class="inline-block rounded-xl px-4 py-2 bg-gradient-to-r from-amber-500 to-orange-500 text-white font-bold shadow-lg">
                Digital Creative Director & Brand Strategist
              </div>
              <p class="text-gray-600">With over a decade of experience in digital design and marketing, I help brands tell their stories through compelling visuals and strategic thinking.</p>
              <p class="text-gray-600">My approach combines creative innovation with data-driven insights, ensuring every project delivers both aesthetic excellence and measurable results.</p>
              
              <div class="mt-8">
                <span class="font-serif text-2xl italic text-amber-600">Dandi Kitessa</span>
              </div>
            </div>
          </div>
        </div>
        <!-- Skills & Social Column -->
        <div class="space-y-8">
          <!-- Skills Matrix -->
          <div class="relative group">
            <div class="absolute inset-0 bg-gradient-to-br from-white/50 to-white/30 backdrop-blur-md rounded-2xl border border-white/20 shadow-lg transition-all duration-300 group-hover:scale-[1.01] group-hover:shadow-xl"></div>
            
            <div class="relative p-8">
              <h3 class="text-2xl font-bold mb-8 bg-gradient-to-r from-amber-500 to-orange-500 bg-clip-text text-transparent">Expertise</h3>
              <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div 
                  v-for="(skill, index) in skills" 
                  :key="index"
                  class="skill-container"
                >
                  <div class="flex justify-between mb-2">
                    <span class="font-medium text-gray-700">{{ skill.name }}</span>
                    <span class="font-medium text-amber-600">{{ skill.level }}%</span>
                  </div>
                  <div class="h-3 rounded-full bg-gray-100 overflow-hidden">
                    <div 
                      class="h-full rounded-full bg-gradient-to-r from-amber-500 to-orange-500 transform-gpu"
                      :style="{ width: `${skill.level}%` }"
                    ></div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <!-- Social Links -->
          <div class="relative group">
            <div class="absolute inset-0 bg-gradient-to-br from-white/50 to-white/30 backdrop-blur-md rounded-2xl border border-white/20 shadow-lg transition-all duration-300 group-hover:scale-[1.01] group-hover:shadow-xl"></div>
            
            <div class="relative p-8">
              <h3 class="text-2xl font-bold mb-8 bg-gradient-to-r from-amber-500 to-orange-500 bg-clip-text text-transparent">Connect With Me</h3>
              <div class="flex flex-wrap gap-4">
                <a 
                  v-for="(social, index) in socialLinks" 
                  :key="index"
                  :href="social.url"
                  class="flex items-center px-4 py-2 rounded-xl bg-white/80 backdrop-blur-sm border border-white/20 shadow-sm transition-all duration-300 hover:scale-105 hover:shadow-lg hover:bg-gradient-to-r hover:from-amber-500 hover:to-orange-500 group"
                >
                  <font-awesome-icon 
                    :icon="['fab', social.icon]" 
                    class="w-5 h-5 text-amber-600 transition-colors duration-300"
                  />
                  <span class="ml-2 font-medium text-gray-700 transition-colors duration-300">{{ social.name }}</span>
                </a>
              </div>
            </div>
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
  name: 'AboutSection',
  components: {
    FontAwesomeIcon
  },
  data() {
    return {
      skills: [
        { name: 'Brand Strategy', level: 95 },
        { name: 'Visual Design', level: 90 },
        { name: 'Digital Marketing', level: 85 },
        { name: 'Photography', level: 88 },
        { name: 'Video Production', level: 82 },
        { name: 'Data Analysis', level: 78 }
      ],
      socialLinks: [
        { name: 'Instagram', icon: 'instagram', url: 'https://www.instagram.com/dandi_digital_marketing_agency' },
        { name: 'LinkedIn', icon: 'linkedin', url: 'https://www.linkedin.com/in/dandi-digital-827b12350' },
        { name: 'Facebook', icon: 'facebook', url: 'https://www.facebook.com/profile.php?id=100082760081622' },
        { name: 'Telegram', icon: 'telegram', url: '#' },
      ]
    }
  }
}
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
@keyframes slideRight {
  to { transform: translateX(0); }
}
.skill-container:hover .h-3 {
  transform: scale(1.02);
}
/* Adjustments for portrait image */
@media (max-width: 768px) {
  .grid { gap: 2rem; }
  .p-8 { padding: 1.5rem; }
  .w-48.h-64.md\:w-64.md\:h-96 {
    aspect-ratio: 2 / 3; /* Maintain portrait aspect ratio */
  }
}
</style>