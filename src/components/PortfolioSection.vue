<template>
  <section id="portfolio" class="min-h-screen relative overflow-hidden bg-gradient-to-br from-indigo-50/90 via-violet-50/80 to-purple-50/90">
    <!-- Hexagonal Background Pattern -->
    <div class="absolute inset-0 opacity-10">
      <div 
        class="absolute inset-0" 
        style="background-image: url('data:image/svg+xml,%3Csvg width=%2260%22 height=%2260%22 viewBox=%220 0 60 60%22 xmlns=%22http://www.w3.org/2000/svg%22%3E%3Cpath d=%22M30 0l25.98 15v30L30 60 4.02 45V15z%22 fill-rule=%22evenodd%22 stroke=%22%234D27F7%22 stroke-width=%220.5%22 fill=%22none%22/%3E%3C/svg%3E');
        background-size: 60px 60px;"
      ></div>
      <div 
        class="absolute inset-0 rotate-30" 
        style="background-image: url('data:image/svg+xml,%3Csvg width=%2260%22 height=%2260%22 viewBox=%220 0 60 60%22 xmlns=%22http://www.w3.org/2000/svg%22%3E%3Cpath d=%22M30 0l25.98 15v30L30 60 4.02 45V15z%22 fill-rule=%22evenodd%22 stroke=%22%23FF3366%22 stroke-width=%220.5%22 fill=%22none%22/%3E%3C/svg%3E');
        background-size: 48px 48px;"
      ></div>
    </div>

    <!-- Glassmorphic Orbs -->
    <div class="absolute inset-0 pointer-events-none overflow-hidden">
      <div class="absolute top-1/4 -right-20 w-[40rem] h-[40rem] bg-gradient-to-br from-indigo-300/20 to-violet-300/20 rounded-full blur-3xl animate-float-slow"></div>
      <div class="absolute -bottom-32 -left-32 w-[50rem] h-[50rem] bg-gradient-to-tr from-purple-300/20 to-fuchsia-300/20 rounded-full blur-3xl animate-float-delay"></div>
    </div>

    <div class="container mx-auto px-6 py-24 relative z-10">
      <!-- Section Header -->
      <div class="text-center mb-16">
        <div class="inline-block bg-white/70 backdrop-blur-sm rounded-full px-6 py-2 mb-6 shadow-lg transform hover:scale-105 transition-all duration-300">
          <span class="text-lg font-bold bg-gradient-to-r from-indigo-500 to-violet-500 bg-clip-text text-transparent">
            Our Portfolio
          </span>
        </div>
        <h2 class="text-5xl md:text-6xl font-black mb-8 tracking-tight">
          <span class="block bg-gradient-to-r from-indigo-500 to-violet-500 bg-clip-text text-transparent">
            Featured Projects
          </span>
        </h2>

        <!-- Filter Navigation -->
        <div class="filter-nav flex flex-wrap justify-center gap-4 mb-12">
          <button 
            v-for="category in categories" 
            :key="category"
            @click="filterProjects(category)"
            class="filter-btn px-6 py-3 rounded-xl font-medium transition-all duration-300 bg-white/50 backdrop-blur-sm border border-white/20 hover:bg-white/80 hover:shadow-lg"
            :class="{ 'active-filter': currentFilter === category }"
          >
            {{ category }}
          </button>
        </div>
      </div>

      <!-- Projects Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <article 
          v-for="project in filteredProjects" 
          :key="project.id"
          class="group relative"
        >
          <!-- Card Background -->
          <div class="absolute inset-0 bg-gradient-to-br from-white/50 to-white/30 backdrop-blur-md rounded-2xl border border-white/20 shadow-lg transition-all duration-300 group-hover:scale-[1.02] group-hover:shadow-xl"></div>
          
          <!-- Project Content -->
          <div class="relative p-6">
            <!-- Image Container -->
            <div class="relative overflow-hidden rounded-xl mb-6">
              <div class="aspect-w-16 aspect-h-12">
                <img 
                  :src="project.image" 
                  :alt="project.title"
                  class="object-cover w-full h-full transform group-hover:scale-105 transition-transform duration-700"
                />
              </div>
              <!-- Tech Stack -->
              <div class="absolute top-4 right-4 flex flex-wrap gap-2">
                <span 
                  v-for="tech in project.technologies" 
                  :key="tech"
                  class="px-3 py-1 rounded-full text-sm font-medium bg-white/80 backdrop-blur-sm shadow-sm"
                >
                  {{ tech }}
                </span>
              </div>
            </div>

            <!-- Project Info -->
            <h3 class="text-2xl font-bold mb-2 bg-gradient-to-r from-indigo-500 to-violet-500 bg-clip-text text-transparent">
              {{ project.title }}
            </h3>
            <p class="text-gray-600 mb-4">{{ project.description }}</p>
            
            <!-- Tags and CTA -->
            <div class="flex justify-between items-center">
              <div class="flex gap-2">
                <span 
                  v-for="tag in project.tags" 
                  :key="tag"
                  class="px-3 py-1 rounded-full text-sm font-medium bg-indigo-100/50 text-indigo-600"
                >
                  {{ tag }}
                </span>
              </div>
              <button class="px-4 py-2 rounded-xl bg-gradient-to-r from-indigo-500 to-violet-500 text-white font-medium transform transition-all duration-300 hover:scale-105 hover:shadow-lg group-hover:translate-x-1">
                View →
              </button>
            </div>
          </div>
        </article>
      </div>

      <!-- Pagination -->
      <div class="pagination mt-16 flex justify-center items-center gap-3">
        <button 
          v-for="page in totalPages" 
          :key="page"
          @click="currentPage = page"
          class="w-10 h-10 rounded-xl font-medium flex items-center justify-center transition-all duration-300 bg-white/50 backdrop-blur-sm border border-white/20 hover:bg-white/80"
          :class="{ 'active-page': currentPage === page }"
        >
          {{ page }}
        </button>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'PortfolioSection',
  data() {
    return {
      currentFilter: 'All',
      currentPage: 1,
      itemsPerPage: 6,
      categories: ['All', 'Design', 'Development', 'Branding', 'Video'],
      projects: [
        {
          id: 1,
          title: 'Brand Evolution',
          description: 'Complete brand identity redesign for a tech startup.',
          image: 'https://laurabusche.com/wp-content/uploads/2016/09/brand-identity-design-custommade.jpeg',
          category: 'Branding',
          technologies: ['Figma', 'PS', 'AI'],
          tags: ['Identity', 'Digital']
        },
        {
          id: 2,
          title: 'E-commerce Platform',
          description: 'Custom e-commerce solution with advanced features.',
          image: 'https://magesolution.com/wp-content/uploads/2022/07/ecommerce-website-design-examples-1024x768.jpg',
          category: 'Development',
          technologies: ['Vue', 'Firebase'],
          tags: ['Web', 'E-commerce']
        }
      ]
    }
  },
  computed: {
    filteredProjects() {
      let filtered = this.currentFilter === 'All' 
        ? this.projects 
        : this.projects.filter(p => p.category === this.currentFilter);
      
      const start = (this.currentPage - 1) * this.itemsPerPage;
      const end = start + this.itemsPerPage;
      return filtered.slice(start, end);
    },
    totalPages() {
      return Math.ceil(this.projects.length / this.itemsPerPage);
    }
  },
  methods: {
    filterProjects(category) {
      this.currentFilter = category;
      this.currentPage = 1;
    }
  }
}
</script>

<style scoped>
.active-filter {
  background-image: linear-gradient(to right, rgb(99 102 241), rgb(139 92 246));
  color: white;
  box-shadow: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);
}

.active-page {
  background-image: linear-gradient(to right, rgb(99 102 241), rgb(139 92 246));
  color: white;
}

@keyframes float-slow {
  0%, 100% { transform: translate(0, 0) rotate(0deg); }
  50% { transform: translate(-20px, 20px) rotate(1deg); }
}

@keyframes float-delay {
  0%, 100% { transform: translate(0, 0) rotate(0deg); }
  50% { transform: translate(20px, -20px) rotate(-1deg); }
}

.animate-float-slow {
  animation: float-slow 15s ease-in-out infinite;
}

.animate-float-delay {
  animation: float-delay 18s ease-in-out infinite;
}

/* Entrance Animations */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

article {
  animation: fadeInUp 0.6s ease-out forwards;
  animation-delay: calc(var(--index) * 0.1s);
}
</style>
