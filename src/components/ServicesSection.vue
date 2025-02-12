<template>
  <section id="services" class="min-h-screen relative overflow-hidden bg-gradient-to-br from-cyan-50/90 via-blue-50/80 to-purple-50/90">
    <!-- Complex Background Pattern -->
    <div class="absolute inset-0 opacity-10">
      <div class="absolute inset-0" style="background-image: radial-gradient(circle at 2px 2px, #00C6BE 1px, transparent 0); background-size: 32px 32px;"></div>
      <div class="absolute inset-0 rotate-45" style="background-image: radial-gradient(circle at 2px 2px, #4D27F7 1px, transparent 0); background-size: 24px 24px;"></div>
    </div>

    <!-- Large Circular Glassmorphic Elements -->
    <div class="absolute inset-0 pointer-events-none overflow-hidden">
      <div class="absolute -top-32 -right-32 w-96 h-96 bg-gradient-to-br from-cyan-300/20 to-blue-300/20 rounded-full blur-3xl"></div>
      <div class="absolute -bottom-40 -left-40 w-[32rem] h-[32rem] bg-gradient-to-tr from-purple-300/20 to-blue-300/20 rounded-full blur-3xl"></div>
    </div>

    <!-- Content Container -->
    <div class="container mx-auto px-6 py-20 relative z-10">
      <!-- Section Header -->
      <div class="text-center mb-16">
        <div class="inline-block bg-white/70 backdrop-blur-sm rounded-full px-6 py-2 mb-6 shadow-lg transform hover:scale-105 transition-all duration-300">
          <span class="text-lg font-bold bg-gradient-to-r from-cyan-500 to-blue-500 bg-clip-text text-transparent">
            Our Services
          </span>
        </div>
        <h2 class="text-5xl md:text-6xl font-black mb-6 tracking-tight">
          <span class="block bg-gradient-to-r from-cyan-500 to-blue-500 bg-clip-text text-transparent">
            Transforming Vision
          </span>
          <span class="block text-blue-400 mt-2">
            Into Digital Reality
          </span>
        </h2>
      </div>

      <!-- Services Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div 
          v-for="(service, index) in services" 
          :key="index"
          class="group relative"
        >
          <!-- Card Background -->
          <div class="absolute inset-0 bg-gradient-to-br from-white/50 to-white/30 backdrop-blur-md rounded-2xl border border-white/20 shadow-lg transition-all duration-300 group-hover:scale-[1.02] group-hover:shadow-xl"></div>
          
          <!-- Card Content -->
          <div class="relative p-8">
            <div class="mb-6 transition-transform duration-300 group-hover:scale-110">
              <component 
                :is="service.icon" 
                class="w-12 h-12"
                :class="`text-gradient-${index % 4}`"
              />
            </div>

            <h3 class="text-2xl font-bold mb-4 bg-gradient-to-r from-cyan-500 to-blue-500 bg-clip-text text-transparent">
              {{ service.title }}
            </h3>
            <p class="text-gray-600 mb-6">{{ service.description }}</p>

            <!-- Tags -->
            <div class="flex flex-wrap gap-2">
              <span 
                v-for="(tag, tagIndex) in service.tags" 
                :key="tagIndex"
                class="px-3 py-1 rounded-full text-sm font-medium bg-white/50 backdrop-blur-sm border border-white/20 shadow-sm transition-all duration-300 hover:scale-105"
              >
                {{ tag }}
              </span>
            </div>
          </div>
        </div>
      </div>

      <!-- Floating Skills -->
      <div class="mt-16 flex flex-wrap justify-center gap-4">
        <div 
          v-for="(skill, index) in floatingSkills" 
          :key="index"
          class="skill-float px-6 py-3 rounded-xl bg-white/70 backdrop-blur-sm shadow-lg border border-white/20"
          :style="{ animationDelay: `${index * 0.2}s` }"
        >
          <span class="font-medium bg-gradient-to-r from-cyan-500 to-blue-500 bg-clip-text text-transparent">
            {{ skill }}
          </span>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { 
  PaintBrushIcon,
  VideoCameraIcon,
  MegaphoneIcon,
  MagnifyingGlassIcon,
  ChartBarIcon,
  ChatBubbleLeftRightIcon,
  ComputerDesktopIcon,
  UserGroupIcon
} from '@heroicons/vue/24/outline'

export default {
  name: 'ServicesSection',
  components: {
    PaintBrushIcon,
    VideoCameraIcon,
    MegaphoneIcon,
    MagnifyingGlassIcon,
    ChartBarIcon,
    ChatBubbleLeftRightIcon,
    ComputerDesktopIcon,
    UserGroupIcon
  },
  data() {
    return {
      services: [
        {
          title: 'Creative Design',
          icon: 'PaintBrushIcon',
          description: 'Crafting visually stunning designs that capture attention and communicate your brand story effectively.',
          tags: ['UI/UX', 'Graphic Design', 'Illustration']
        },
        {
          title: 'Branding',
          icon: 'PaintBrushIcon',
          description: 'Building distinctive brand identities that resonate with your audience and stand out in the market.',
          tags: ['Identity Design', 'Brand Strategy', 'Guidelines']
        },
        {
          title: 'Video Production',
          icon: 'VideoCameraIcon',
          description: 'Creating compelling video content that engages viewers and delivers your message with impact.',
          tags: ['Editing', 'Animation', 'Production']
        },
        {
          title: 'SEO Optimization',
          icon: 'MagnifyingGlassIcon',
          description: 'Improving your digital visibility and driving organic traffic through strategic SEO implementation.',
          tags: ['Technical SEO', 'Content Strategy', 'Analytics']
        },
        {
          title: 'Data Analysis',
          icon: 'ChartBarIcon',
          description: 'Transforming raw data into actionable insights to drive informed business decisions.',
          tags: ['Visualization', 'Reporting', 'Insights']
        },
        {
          title: 'Social Media',
          icon: 'ChatBubbleLeftRightIcon',
          description: 'Managing your social presence to build community and drive engagement.',
          tags: ['Strategy', 'Content', 'Management']
        },
        {
          title: 'Web Development',
          icon: 'ComputerDesktopIcon',
          description: 'Building responsive, modern websites that deliver exceptional user experiences.',
          tags: ['Frontend', 'Backend', 'UX Design']
        },
        {
          title: 'Influencer Marketing',
          icon: 'UserGroupIcon',
          description: 'Connecting brands with relevant influencers to expand reach and authenticity.',
          tags: ['Partnerships', 'Campaign', 'Analytics']
        }
      ],
      floatingSkills: [
        'SEO Architecture',
        'Conversion Funnels',
        'UI Sorcery',
        'Brand DNA Mapping',
        'Content Catalysts',
        'Data Alchemy'
      ]
    }
  }
}
</script>

<style scoped>
.text-gradient-0 {
  background: linear-gradient(to right, #00C6BE, #4D27F7);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.text-gradient-1 {
  background: linear-gradient(to right, #4D27F7, #FF3366);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.text-gradient-2 {
  background: linear-gradient(to right, #FF3366, #FFDE59);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.text-gradient-3 {
  background: linear-gradient(to right, #FFDE59, #00C6BE);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

@keyframes skillFloat {
  0%, 100% {
    transform: translateY(0) rotate(0);
  }
  50% {
    transform: translateY(-10px) rotate(2deg);
  }
}

.skill-float {
  animation: skillFloat 4s ease-in-out infinite;
}

.skill-float:nth-child(even) {
  animation-duration: 5s;
  animation-direction: reverse;
}
</style>