<script setup>
import HeroSection from '../components/HeroSection.vue'
import NavBar from '../components/NavBar.vue'
import ServicesSection from '../components/ServicesSection.vue'
import PortfolioSection from '../components/PortfolioSection.vue'
import AboutSection from '../components/AboutSection.vue'
import ContactSection from '../components/ContactSection.vue'
import FooterSection from '../components/FooterSection.vue'
</script>

<template>
  <div class="home">
    <NavBar />
    <HeroSection />
    <ServicesSection />
    <PortfolioSection />
    <AboutSection />
    <ContactSection />
    <FooterSection />
  </div>
</template>

<style>
.home {
  background-color: #FFDE59;
  min-height: 100vh;
}
</style>
