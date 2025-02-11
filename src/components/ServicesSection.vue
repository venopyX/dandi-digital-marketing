<template>
  <section id="services" class="services-section py-20 bg-[#00C6BE] relative overflow-hidden">
    <!-- Background Pattern -->
    <div class="absolute inset-0 bg-grid opacity-5"></div>
    
    <!-- Content Container -->
    <div class="container mx-auto px-6">
      <!-- Section Header -->
      <div class="section-header mb-16 relative">
        <span class="inline-block text-xl font-mono mb-4 px-4 py-2 bg-black text-white border-[6px] border-black transform -rotate-2">What We Do</span>
        <h2 class="text-5xl md:text-6xl font-black mb-6 relative">
          <span class="inline-block bg-white px-6 py-3 border-[6px] border-black shadow-brutal transform rotate-1">Our Services</span>
        </h2>
        <p class="text-xl text-black max-w-2xl mt-8 bg-[#FFDE59] p-4 border-[6px] border-black shadow-brutal inline-block transform -rotate-1">
          Transforming visions into digital reality through innovative design and strategic solutions.
        </p>
      </div>

      <!-- Services Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div 
          v-for="(service, index) in services" 
          :key="index"
          class="service-card bg-white border-[6px] border-black shadow-brutal transform hover:-rotate-1 hover:translate-x-2 hover:-translate-y-2 transition-transform"
          :class="[`accent-${index % 4}`]"
        >
          <!-- Service Icon -->
          <div class="icon-container mb-6">
            <component 
              :is="service.icon" 
              class="w-12 h-12 text-white"
            />
          </div>

          <!-- Service Content -->
          <h3 class="text-2xl font-black mb-4">{{ service.title }}</h3>
          <p class="text-gray-800 mb-6 font-medium">{{ service.description }}</p>

          <!-- Skills Tags -->
          <div class="flex flex-wrap gap-2">
            <span 
              v-for="(tag, tagIndex) in service.tags" 
              :key="tagIndex"
              class="skill-tag inline-block"
            >
              {{ tag }}
            </span>
          </div>
        </div>
      </div>

      <!-- Floating Skills -->
      <div class="skills-cloud mt-16 flex flex-wrap justify-center gap-6">
        <div 
          v-for="(skill, index) in floatingSkills" 
          :key="index"
          class="floating-skill bg-[#FF3366] text-white font-bold py-3 px-6 border-[6px] border-black shadow-brutal transform hover:rotate-3 hover:-translate-y-2 transition-transform"
          :style="{ animationDelay: `${index * 0.2}s` }"
        >
          {{ skill }}
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
/* Background Grid Pattern */
.bg-grid {
  background-image: linear-gradient(to right, #000 2px, transparent 2px),
                    linear-gradient(to bottom, #000 2px, transparent 2px);
  background-size: 48px 48px;
}

/* Service Cards */
.service-card {
  padding: 2rem;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.shadow-brutal {
  box-shadow: 8px 8px 0 rgba(0, 0, 0, 1);
}

/* Accent Colors */
.accent-0 .icon-container { background-color: #FF3366; }
.accent-1 .icon-container { background-color: #4D27F7; }
.accent-2 .icon-container { background-color: #00C6BE; }
.accent-3 .icon-container { background-color: #FFDE59; }

/* Skill Tags */
.skill-tag {
  padding: 0.25rem 0.75rem;
  background-color: #4D27F7;
  color: white;
  font-size: 0.875rem;
  font-family: monospace;
  font-weight: bold;
  border: 4px solid black;
  transform: rotate(-1deg);
  transition: transform 0.3s ease;
}

.skill-tag:hover {
  transform: rotate(2deg) scale(1.05);
}

/* Icon Container */
.icon-container {
  padding: 1rem;
  display: inline-block;
  border: 6px solid black;
  transform: rotate(-6deg);
  transition: transform 0.3s ease;
}

.service-card:hover .icon-container {
  transform: rotate(6deg);
}

@keyframes float {
  0%, 100% {
    transform: translateY(0) rotate(-2deg);
  }
  50% {
    transform: translateY(-15px) rotate(2deg);
  }
}

/* Responsive Adjustments */
@media (max-width: 768px) {
  .service-card {
    transform: none !important;
  }
  
  .shadow-brutal {
    box-shadow: 6px 6px 0 rgba(0, 0, 0, 1);
  }
  
  .floating-skill {
    transform: none;
  }
  
  .section-header h2 {
    font-size: 2.5rem;
  }
  
  .section-header p {
    font-size: 1.125rem;
  }
}
</style>