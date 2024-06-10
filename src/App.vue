<template>
  <div id="luxy" class="wrapp">
    <section class="sticky">
      <HeaderSection />
    </section>

    <AboutSection />
    <BenefitsSection />
    <WorkSection />
    <ServicesSection />

    <FooterSection />
  </div>
</template>

<script>
import { onMounted } from "vue";
import luxy from "luxy.js";
import Splitting from "splitting";
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

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

      gsap.to(".sticky", {
        scrollTrigger: {
          trigger: ".sticky",
          start: "top top",
          end: () =>
            "+=" +
            (window.innerHeight +
              document.querySelector(".about").offsetHeight * 0.75),
          scrub: 1,
          pin: true,
        },
        y: 250,
        scale: 0.75,
        rotation: -15,
        ease: "ease.out",
      });
    });
  },
};
</script>
<style>
@import "splitting/dist/splitting.css";
@import "splitting/dist/splitting-cells.css";
@import "./assets/styles.css"; /* Bu CSS dosyası aşağıda oluşturulacak */

img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

#app {
  width: 100%;
  height: 100%;
}

section.sticky {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: #5546ff;
}

@media (max-width: 900px) {
  .header {
    top: 80%;
  }

  section.main {
    height: max-content;
  }

  .row {
    flex-direction: column;
  }
}
</style>
