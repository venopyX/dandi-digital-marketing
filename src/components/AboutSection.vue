<template>
  <section id="about" class="about-section py-24 relative overflow-hidden bg-[#FFDE59]">
    <!-- Decorative Elements -->
    <div class="absolute inset-0 bg-grid opacity-5"></div>
    
    <div class="container mx-auto px-6">
      <!-- Section Header -->
      <div class="mb-16">
        <span class="inline-block px-6 py-3 bg-black text-white font-mono mb-4 transform -rotate-2 border-[6px] border-black shadow-brutal">
          About Us
        </span>
        <h2 class="text-5xl md:text-6xl font-black relative inline-block bg-white px-6 py-3 border-[6px] border-black shadow-brutal transform rotate-1">
          Meet Dandi
        </h2>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12">
        <!-- Biography Column -->
        <div class="biography-container">
          <!-- Profile Image -->
          <div class="profile-image-wrapper mb-8 lg:float-right lg:ml-8 lg:mb-4">
            <div class="relative inline-block">
              <div class="w-48 h-48 md:w-64 md:h-64 border-[6px] border-black overflow-hidden transform rotate-3 shadow-brutal bg-white">
                <img 
                  src="https://placehold.co/400x400" 
                  alt="Dandi Kitessa"
                  class="w-full h-full object-cover"
                />
              </div>
              <div class="absolute -bottom-4 -right-4 w-full h-full border-[6px] border-black bg-[#FF3366] -z-10"></div>
            </div>
          </div>

          <!-- Biography Text -->
          <div class="biography-text space-y-6 text-lg bg-white p-6 border-[6px] border-black shadow-brutal transform hover:-rotate-1 transition-transform">
            <p class="font-black text-xl px-4 py-2 bg-[#4D27F7] text-white inline-block transform -rotate-1">Digital Creative Director & Brand Strategist</p>
            <p class="font-medium">With over a decade of experience in digital design and marketing, I help brands tell their stories through compelling visuals and strategic thinking.</p>
            <p class="font-medium">My approach combines creative innovation with data-driven insights, ensuring every project delivers both aesthetic excellence and measurable results.</p>
            
            <!-- Signature Element -->
            <div class="signature-block mt-8">
              <div class="w-32 h-16 bg-contain bg-no-repeat bg-left transform -rotate-3">
                <!-- Placeholder for signature -->
                <span class="font-handwriting text-2xl">Dandi Kitessa</span>
              </div>
            </div>
          </div>
        </div>

        <!-- Skills & Social Column -->
        <div class="space-y-12">
          <!-- Skills Matrix -->
          <div class="skills-matrix p-8 border-[6px] border-black bg-white transform hover:-translate-y-2 hover:translate-x-2 transition-transform shadow-brutal">
            <h3 class="text-2xl font-black mb-6 px-4 py-2 bg-[#00C6BE] text-white inline-block transform -rotate-1 border-[4px] border-black">Expertise</h3>
            <div class="grid grid-cols-2 gap-4">
              <template v-for="(skill, index) in skills" :key="index">
                <div class="skill-bar-container">
                  <div class="flex justify-between mb-2">
                    <span class="font-mono font-bold text-sm">{{ skill.name }}</span>
                    <span class="font-mono font-bold text-sm">{{ skill.level }}%</span>
                  </div>
                  <div class="h-6 border-[4px] border-black bg-white">
                    <div 
                      class="h-full bg-[#FF3366]"
                      :style="{ width: `${skill.level}%` }"
                    ></div>
                  </div>
                </div>
              </template>
            </div>
          </div>

          <!-- Social Links -->
          <div class="social-panel bg-white p-6 border-[6px] border-black shadow-brutal transform hover:translate-x-2 hover:-translate-y-2 transition-transform">
            <h3 class="text-2xl font-black mb-6 px-4 py-2 bg-[#4D27F7] text-white inline-block transform -rotate-1 border-[4px] border-black">Connect With Me</h3>
            <div class="flex flex-wrap gap-4">
              <a 
                v-for="(social, index) in socialLinks" 
                :key="index"
                :href="social.url"
                class="social-link flex items-center px-4 py-2 border-[4px] border-black bg-[#FFDE59] hover:bg-[#FF3366] hover:text-white font-bold transition-colors shadow-brutal transform hover:-rotate-2"
                :title="social.name"
              >
                <component 
                  :is="social.icon" 
                  class="w-6 h-6"
                />
                <span class="ml-2 font-mono">{{ social.name }}</span>
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { 
  UserGroupIcon,
  HashtagIcon,
  GlobeAltIcon,
  RssIcon
} from '@heroicons/vue/24/outline'

export default {
  name: 'AboutSection',
  components: {
    UserGroupIcon,
    HashtagIcon,
    GlobeAltIcon,
    RssIcon
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
        { name: 'Community', icon: 'UserGroupIcon', url: '#' },
        { name: 'Social', icon: 'HashtagIcon', url: '#' },
        { name: 'Website', icon: 'GlobeAltIcon', url: '#' },
        { name: 'Blog', icon: 'RssIcon', url: '#' }
      ]
    }
  }
}
</script>

<style scoped>
.bg-grid {
  background-image: linear-gradient(to right, #000 2px, transparent 2px),
                   linear-gradient(to bottom, #000 2px, transparent 2px);
  background-size: 48px 48px;
}

.shadow-brutal {
  box-shadow: 8px 8px 0 rgba(0, 0, 0, 1);
}

.profile-image-wrapper {
  position: relative;
  display: inline-block;
  filter: grayscale(20%);
  transition: all 0.3s ease;
}

.profile-image-wrapper:hover {
  filter: grayscale(0%);
  transform: rotate(-2deg);
}

.biography-text {
  line-height: 1.6;
}

.font-handwriting {
  font-family: 'Permanent Marker', cursive;
  font-size: 2rem;
}

.skill-bar-container:hover .h-6 {
  transform: translate(-2px, -2px);
  box-shadow: 4px 4px 0 rgba(0, 0, 0, 1);
}

/* Responsive Adjustments */
@media (max-width: 768px) {
  .shadow-brutal {
    box-shadow: 6px 6px 0 rgba(0, 0, 0, 1);
  }
  
  .grid-cols-2 {
    grid-template-columns: 1fr;
  }
  
  .biography-text,
  .skills-matrix,
  .social-panel {
    transform: none !important;
  }
}
</style>