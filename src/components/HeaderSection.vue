<template>
  <header class="header">
    <h1 class="title" data-splitting>
      <span class="title_paralax">Parallax effect</span
      ><span class="stroke">on gsap</span>
    </h1>
    <div class="header__img">
      <img
        src="https://dmitrinaumov.github.io/Paralax-effect-with-gsap-scrolltrigger/img/1.jpg"
        alt="1"
      />
    </div>
    <div class="header__marq">
      <div class="header__marq-wrapp">
        <span class="header__marq-txt"
          >discuss your ideas
          <span class="header__marq-star">
            <img
              src="https://dmitrinaumov.github.io/Paralax-effect-with-gsap-scrolltrigger/img/star.svg"
              alt=""
            />
          </span>
        </span>
        <span class="header__marq-txt"
          >discuss your ideas
          <span class="header__marq-star">
            <img
              src="https://dmitrinaumov.github.io/Paralax-effect-with-gsap-scrolltrigger/img/star.svg"
              alt=""
            />
          </span>
        </span>
        <span class="header__marq-txt"
          >discuss your ideas
          <span class="header__marq-star">
            <img
              src="https://dmitrinaumov.github.io/Paralax-effect-with-gsap-scrolltrigger/img/star.svg"
              alt=""
            />
          </span>
        </span>
        <span class="header__marq-txt"
          >discuss your ideas
          <span class="header__marq-star">
            <img
              src="https://dmitrinaumov.github.io/Paralax-effect-with-gsap-scrolltrigger/img/star.svg"
              alt=""
            />
          </span>
        </span>
      </div>
    </div>
  </header>
</template>

<script>
import { onMounted } from "vue";
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

export default {
  name: "HeaderSection",
  setup() {
    onMounted(() => {
      const gTl = gsap.timeline();
      gTl.from(".title .char", {
        opacity: 0,
        yPercent: 130,
        stagger: 0.06,
        ease: "back.out",
      });
      gTl.to(
        ".header__img",
        {
          clipPath: "polygon(0% 0%, 100% 0%, 100% 100%, 0% 100%)",
          scale: 1,
          ease: "expo.out",
        },
        "-=1"
      );
      gTl.from(
        ".header__marq",
        { opacity: 0, yPercent: 100, ease: "expo.out" },
        "-=1.5"
      );

      gsap.utils.toArray(".section-title__square").forEach((gSq) => {
        const rotat = gsap.from(gSq, { rotation: 720 });
        ScrollTrigger.create({
          trigger: gSq,
          animation: rotat,
          start: "top bottom",
          scrub: 1.9,
        });
      });

      function initAnimations() {
        gsap.to(".title_paralax", {
          scrollTrigger: {
            trigger: ".header",
            start: "top top",
            scrub: 1.9,
          },
          yPercent: -150,
        });
        gsap.to(".header .stroke", {
          scrollTrigger: {
            trigger: ".header",
            start: "top top",
            scrub: 1.9,
          },
          xPercent: 50,
        });
        gsap.to(".header__img", {
          scrollTrigger: {
            trigger: ".header",
            start: "top top",
            scrub: 1.9,
          },
          xPercent: -70,
        });
        gsap.to(".header__img img", {
          scrollTrigger: {
            trigger: ".header",
            start: "top top",
            scrub: 1.9,
          },
          scale: 1.3,
        });
        gsap.to(".header__marq-wrapp", {
          scrollTrigger: {
            trigger: ".header",
            start: "top top",
            scrub: 1.9,
          },
          xPercent: -50,
        });
        gsap.to(".header__marq-star img", {
          scrollTrigger: {
            trigger: ".header",
            start: "top top",
            scrub: 1.9,
          },
          rotate: -720,
        });
      }

      initAnimations();
    });
  },
};
</script>

<style scoped>
@import url(../assets/styles.css);
</style>
