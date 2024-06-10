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
      gsap.fromTo(
        ".about",
        {
          x: -100,
          scale: 0.3,
          rotation: 15,
        },
        {
          scrollTrigger: {
            trigger: ".about",
            start: "top 200%",
            end: "top 50%",
            scrub: 1,
          },
          x: 0,
          scale: 1,
          rotation: 0,
          ease: "power3.out",
        }
      );
    });
  },
};
</script>
<style scoped>
@import url(../assets/styles.css);
.about {
  width: 100%;
  height: 100vh;
  background: #252525;
  padding: 6em 2em;
}
</style>
