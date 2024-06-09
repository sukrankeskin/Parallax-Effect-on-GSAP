<template>
  <div id="luxy" class="wrapp">
    <HeaderSection />
    <main class="main">
      <AboutSection />
      <BenefitsSection />
      <WorkSection />
      <ServicesSection />
    </main>
    <FooterSection />
  </div>
</template>

<script>
import { onMounted } from "vue";
import luxy from "luxy.js";
import Splitting from "splitting";

import HeaderSection from "./components/HeaderSection.vue";
import AboutSection from "./components/AboutSection.vue";
import BenefitsSection from "./components/BenefitsSection.vue";
import WorkSection from "./components/WorkSection.vue";
import ServicesSection from "./components/ServicesSection.vue";
import FooterSection from "./components/FooterSection.vue";

export default {
  components: {
    HeaderSection,
    AboutSection,
    BenefitsSection,
    WorkSection,
    ServicesSection,
    FooterSection,
  },
  setup() {
    onMounted(() => {
      Splitting();
      luxy.init();
    });
  },
};
</script>
<style>
@import "splitting/dist/splitting.css";
@import "splitting/dist/splitting-cells.css";
@import "./assets/styles.css"; /* Bu CSS dosyası aşağıda oluşturulacak */
</style>
