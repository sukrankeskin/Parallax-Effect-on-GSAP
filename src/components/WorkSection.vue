<template>
  <section class="work">
    <div class="content">
      <h2 class="section-title">
        portfo<span class="stroke">lio</span>
        <span class="section-title__square"></span>
      </h2>
    </div>

    <div class="work__wrapp">
      <div class="work__item" data-speed="-300">
        <span class="work__item-num" data-speed="-1000">/001</span>
        <div class="work__item-img">
          <img
            src="https://dmitrinaumov.github.io/Paralax-effect-with-gsap-scrolltrigger/img/3.jpg"
            alt="3"
          />
        </div>
      </div>
      <div class="work__item" data-speed="-600">
        <span class="work__item-num" data-speed="-500">/002</span>
        <div class="work__item-img">
          <img
            src="https://dmitrinaumov.github.io/Paralax-effect-with-gsap-scrolltrigger/img/4.jpg"
            alt="4"
          />
        </div>
      </div>
      <div class="work__item" data-speed="-700">
        <span class="work__item-num" data-speed="-700">/003</span>
        <div class="work__item-img">
          <img
            src="https://dmitrinaumov.github.io/Paralax-effect-with-gsap-scrolltrigger/img/5.jpg"
            alt="5"
          />
        </div>
      </div>
      <div class="work__item" data-speed="-400">
        <span class="work__item-num" data-speed="-200">/004</span>
        <div class="work__item-img">
          <img
            src="https://dmitrinaumov.github.io/Paralax-effect-with-gsap-scrolltrigger/img/6.jpg"
            alt="6"
          />
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
  name: "WorkSection",
  setup() {
    onMounted(() => {
      gsap.from(".work__item, .work__item-num", {
        y: (i, el) => 1 - parseFloat(el.getAttribute("data-speed")),
        scrollTrigger: {
          trigger: ".work",
          start: "top bottom",
          scrub: 1.9,
        },
      });
      gsap.from(".work__item-img img", {
        scale: 1.6,
        scrollTrigger: {
          trigger: ".work__wrapp",
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
