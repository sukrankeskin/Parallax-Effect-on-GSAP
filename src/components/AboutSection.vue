<template>
  <section class="about">
    <Animation />
  </section>
</template>

<script>
import { onMounted } from "vue";
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import Animation from "./Animation.vue";

gsap.registerPlugin(ScrollTrigger);

export default {
  name: "AboutSection",
  components: {
    Animation,
  },
  setup() {
    onMounted(() => {
      gsap.from(".about__img", {
        scrollTrigger: {
          trigger: ".about",
          start: "top bottom",
          scrub: 1.9,
        },
        yPercent: 80,
      });
      gsap.from(".about__img img", {
        scrollTrigger: {
          trigger: ".about",
          start: "top bottom",
          scrub: 1.9,
        },
        scale: 1.6,
      });
      gsap.to(".about__txt", {
        scrollTrigger: {
          trigger: ".about__wrapp",
          start: "top bottom",
          scrub: 1.9,
        },
        yPercent: 50,
      });
    });
  },
};
</script>
<style scoped>
@import url(../assets/styles.css);
</style>
