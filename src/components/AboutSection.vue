<template>
  <section class="about">
    <div class="about__wrapp">
      <div class="about__img">
        <img
          src="https://dmitrinaumov.github.io/Paralax-effect-with-gsap-scrolltrigger/img/2.jpg"
          alt="2"
        />
      </div>
      <div class="about__txt">
        <h2 class="section-title">
          abo<span class="stroke">ut</span>
          <span class="section-title__square"></span>
        </h2>
        <p class="about__p">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Cumque esse
          aspernatur fugit debitis quisquam. Quia exercitationem ipsum voluptas
          voluptatum hic enim quo provident culpa possimus cupiditate! Dolorum
          quae doloremque cum rerum ipsam inventore beatae, at odit, velit,
          aspernatur minima! Corporis.
        </p>
      </div>
    </div>
  </section>
</template>

<script>
import { onMounted } from "vue";
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

export default {
  name: "AboutSection",
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
