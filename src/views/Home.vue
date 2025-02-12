<script setup>
import HeroSection from '../components/HeroSection.vue'
import ServicesSection from '../components/ServicesSection.vue'
import PortfolioSection from '../components/PortfolioSection.vue'
import AboutSection from '../components/AboutSection.vue'
import ContactSection from '../components/ContactSection.vue'
import FooterSection from '../components/FooterSection.vue'
</script>

<template>
  <div class="home">
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
  min-height: 100vh;
}
</style>
