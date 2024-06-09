<template>
  <section class="benefits">
    <div class="content">
      <h2 class="section-title">
        benef<span class="stroke">its</span>
        <span class="section-title__square"></span>
      </h2>

      <ul class="benefits__list">
        <li class="benefits__item">
          <span class="benefits__num" data-speed="-200">/01</span>
          <p class="benefits__p">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Omnis,
            quas.
          </p>
        </li>
        <li class="benefits__item">
          <span class="benefits__num" data-speed="-150">/02</span>
          <p class="benefits__p">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Omnis,
            quas.
          </p>
        </li>
        <li class="benefits__item">
          <span class="benefits__num" data-speed="-150">/03</span>
          <p class="benefits__p">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Omnis,
            quas.
          </p>
        </li>
        <li class="benefits__item">
          <span class="benefits__num" data-speed="-150">/04</span>
          <p class="benefits__p">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Omnis,
            quas.
          </p>
        </li>
        <li class="benefits__item">
          <span class="benefits__num" data-speed="-110">/05</span>
          <p class="benefits__p">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Omnis,
            quas.
          </p>
        </li>
        <li class="benefits__item">
          <span class="benefits__num" data-speed="-200">/06</span>
          <p class="benefits__p">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Omnis,
            quas.
          </p>
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
import { onMounted } from "vue";
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

export default {
  name: "BenefitsSection",
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
