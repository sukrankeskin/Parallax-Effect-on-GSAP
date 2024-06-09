<template>
  <footer class="footer">
    <div class="footer__div">
      <span data-speed="-300">a</span>
      <span data-speed="100">p</span>
      <span data-speed="300">p</span>
      <span data-speed="-300">r</span>
      <span data-speed="350">o</span>
      <span data-speed="200">v</span>
      <span data-speed="-310">e</span>
      <span data-speed="200">c</span>
      <span data-speed="-340">o</span>
      <span data-speed="-100">d</span>
      <span data-speed="300">e</span>
    </div>
  </footer>
</template>

<script>
import { onMounted } from "vue";
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

export default {
  name: "FooterSection",
  setup() {
    onMounted(() => {
      gsap.from(".footer__div span", {
        y: (i, el) => 1 - parseFloat(el.getAttribute("data-speed")),
        opacity: 0,
        scrollTrigger: {
          trigger: ".footer",
          start: "top bottom",
          end: "bottom bottom",
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
