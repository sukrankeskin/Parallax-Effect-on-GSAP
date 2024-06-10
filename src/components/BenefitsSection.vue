<template>
  <section class="benefits">
    <ImageComponent />
  </section>
</template>

<script>
import { onMounted } from "vue";
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import ImageComponent from "./ImageComponent.vue";

ScrollTrigger;

export default {
  name: "BenefitsSection",
  components: {
    ImageComponent,
  },
  setup() {
    onMounted(() => {
      gsap.from(".benefits__num", {
        x: (i, el) => 1 - parseFloat(el.getAttribute("data-speed")),
        scrollTrigger: {
          trigger: ".benefits__list",
          start: "top bottom",
          scrub: 1.9,
        },
      });
    });
  },
};
</script>
<style scoped>
@import url(../assets/styles.css);
</style>
