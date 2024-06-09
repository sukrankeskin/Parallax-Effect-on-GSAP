<template>
  <section class="serv">
    <div class="content">
      <h2 class="section-title">
        servic<span class="stroke">es</span>
        <span class="section-title__square"></span>
      </h2>

      <div class="serv__list">
        <div class="serv__item">
          <span class="serv__item-arrow" data-speed="500">
            <img
              src="https://dmitrinaumov.github.io/Paralax-effect-with-gsap-scrolltrigger/img/arrow.svg"
              alt=""
            />
          </span>
          <div class="serv__item-txt">
            <span class="serv__item-text">/Graphic Design</span>
          </div>
        </div>
        <div class="serv__item">
          <span class="serv__item-arrow" data-speed="400">
            <img
              src="https://dmitrinaumov.github.io/Paralax-effect-with-gsap-scrolltrigger/img/arrow.svg"
              alt=""
            />
          </span>
          <div class="serv__item-txt">
            <span class="serv__item-text">/UX/UI Design</span>
          </div>
        </div>
        <div class="serv__item">
          <span class="serv__item-arrow" data-speed="800">
            <img
              src="https://dmitrinaumov.github.io/Paralax-effect-with-gsap-scrolltrigger/img/arrow.svg"
              alt=""
            />
          </span>
          <div class="serv__item-txt">
            <span class="serv__item-text">/Web Design</span>
          </div>
        </div>
        <div class="serv__item">
          <span class="serv__item-arrow" data-speed="600">
            <img
              src="https://dmitrinaumov.github.io/Paralax-effect-with-gsap-scrolltrigger/img/arrow.svg"
              alt=""
            />
          </span>
          <div class="serv__item-txt">
            <span class="serv__item-text">/Brend Design</span>
          </div>
        </div>
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
  name: "ServicesSection",
  setup() {
    onMounted(() => {
      gsap.from(".serv__item-arrow", {
        x: (i, el) => 1 - parseFloat(el.getAttribute("data-speed")),
        scrollTrigger: {
          trigger: ".serv__list",
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
