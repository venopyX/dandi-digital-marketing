<template>
  <section id="portfolio" class="portfolio-section py-24 bg-[#4D27F7] relative">
    <!-- Decorative Background -->
    <div class="absolute inset-0 overflow-hidden">
      <div class="absolute -right-12 top-12 w-64 h-64 bg-[#FFDE59] border-[6px] border-black transform rotate-12 opacity-20"></div>
      <div class="absolute -left-12 bottom-12 w-48 h-48 bg-[#FF3366] border-[6px] border-black transform -rotate-12 opacity-20"></div>
    </div>

    <div class="container mx-auto px-6 relative">
      <!-- Section Header -->
      <div class="mb-16">
        <span class="inline-block px-6 py-3 bg-black text-white font-mono mb-4 transform -rotate-2 border-[6px] border-black shadow-brutal">
          Our Work
        </span>
        <h2 class="text-5xl md:text-6xl font-black mb-8 text-white">
          Featured Projects
        </h2>

        <!-- Filter Navigation -->
        <div class="filter-nav flex flex-wrap gap-4 mb-12">
          <button 
            v-for="category in categories" 
            :key="category"
            @click="filterProjects(category)"
            class="filter-btn px-6 py-3 border-[6px] border-black font-bold transition-all bg-white hover:bg-[#FFDE59] hover:-translate-y-1 hover:translate-x-1 shadow-brutal"
            :class="{ 'active': currentFilter === category }"
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
          class="project-card group"
        >
          <!-- Project Image -->
          <div class="relative overflow-hidden border-[6px] border-black mb-4 shadow-brutal bg-white">
            <div class="aspect-w-16 aspect-h-12 bg-gray-100">
              <img 
                :src="project.image" 
                :alt="project.title"
                class="object-cover w-full h-full transform group-hover:scale-105 transition-transform duration-500"
              />
            </div>
            <!-- Technical Stamps -->
            <div class="absolute top-4 right-4 flex flex-wrap gap-2">
              <span 
                v-for="tech in project.technologies" 
                :key="tech"
                class="tech-stamp px-3 py-2 bg-[#FF3366] text-white border-[4px] border-black text-sm font-mono transform rotate-2 font-bold"
              >
                {{ tech }}
              </span>
            </div>
          </div>

          <!-- Project Info -->
          <div class="p-6 bg-white border-[6px] border-black transform hover:-translate-y-2 hover:translate-x-2 transition-transform shadow-brutal">
            <h3 class="text-2xl font-black mb-2">{{ project.title }}</h3>
            <p class="text-gray-800 mb-4 font-medium">{{ project.description }}</p>
            <div class="flex justify-between items-center">
              <div class="flex gap-2">
                <span 
                  v-for="tag in project.tags" 
                  :key="tag"
                  class="px-3 py-2 bg-[#00C6BE] text-white text-sm font-mono font-bold border-[4px] border-black"
                >
                  {{ tag }}
                </span>
              </div>
              <button class="view-project-btn px-4 py-2 border-[4px] border-black bg-[#FFDE59] hover:bg-[#FF3366] hover:text-white font-bold transition-colors shadow-brutal">
                View →
              </button>
            </div>
          </div>
        </article>
      </div>

      <!-- Pagination -->
      <div class="pagination mt-16 flex justify-center items-center gap-4">
        <button 
          v-for="page in totalPages" 
          :key="page"
          @click="currentPage = page"
          class="pagination-btn w-12 h-12 border-[6px] border-black font-bold flex items-center justify-center transition-all bg-white hover:bg-[#FFDE59] shadow-brutal"
          :class="{ 'active': currentPage === page }"
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
          image: 'https://placehold.co/600x450',
          category: 'Branding',
          technologies: ['Figma', 'PS', 'AI'],
          tags: ['Identity', 'Digital']
        },
        {
          id: 2,
          title: 'E-commerce Platform',
          description: 'Custom e-commerce solution with advanced features.',
          image: 'https://placehold.co/600x450',
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
.shadow-brutal {
  box-shadow: 8px 8px 0 rgba(0, 0, 0, 1);
}

.project-card {
  opacity: 0;
  animation: fadeIn 0.6s ease forwards;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.filter-btn.active {
  background-color: #FFDE59;
  transform: translate(-2px, -2px);
}

.pagination-btn.active {
  background-color: #FFDE59;
  position: relative;
}

.pagination-btn.active::after {
  content: '';
  position: absolute;
  bottom: -8px;
  left: 50%;
  width: 20px;
  height: 4px;
  background: black;
  transform: translateX(-50%);
}

/* Responsive Adjustments */
@media (max-width: 768px) {
  .filter-nav {
    flex-wrap: wrap;
  }
  
  .filter-btn {
    width: 100%;
  }
  
  .project-card {
    animation: none;
    opacity: 1;
  }

  .shadow-brutal {
    box-shadow: 6px 6px 0 rgba(0, 0, 0, 1);
  }
}

/* Print Styles */
@media print {
  .filter-nav,
  .pagination {
    display: none;
  }
  
  .project-card {
    break-inside: avoid;
  }
}
</style>