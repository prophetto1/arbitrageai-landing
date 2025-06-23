<script setup lang="ts">
import { useColorMode } from "@vueuse/core";
mode.value = "dark";

import Navbar from "./components/Navbar.vue";
import Hero from "./components/Hero.vue";
import Features from "./components/Features.vue";
import Benefits from "./components/Benefits.vue";
import Services from "./components/Services.vue";
import Team from "./components/Team.vue";
import Community from "./components/Community.vue";
import Contact from "./components/Contact.vue";
import FAQ from "./components/FAQ.vue";
import Footer from "./components/Footer.vue";
import ScrollToTop from "./components/ScrollToTop.vue";
</script>

<template>
  <Navbar />
  <Hero />
  <Features />
  <Benefits />
  <Team />
  <Services />
  <Community />
  <Contact />
  <FAQ />
  <Footer />
  <ScrollToTop />
</template>
