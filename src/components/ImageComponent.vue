<template>
  <div class="container" ref="container">
    <div class="gallery">
      <div
        class="gallery-item"
        v-for="(image, index) in images"
        :key="index"
        @mouseenter="handleMouseEnter(index)"
        :style="{ flex: imageFlex(index) }"
      >
        <img :src="require(`../assets/img${image}.jpg`)" alt="" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      images: [],
      hoveredIndex: 0,
      defaultItemFlex: "0 1 80px",
      hoverItemFlex: "1 1 400px",
      container: null,
    };
  },
  mounted() {
    this.images = Array.from({ length: 7 }, (_, i) => i + 1);
    this.container = this.$refs.container;
  },
  methods: {
    handleMouseEnter(index) {
      this.hoveredIndex = index;
    },
    imageFlex(index) {
      return index === this.hoveredIndex
        ? this.hoverItemFlex
        : this.defaultItemFlex;
    },
  },
};
</script>

<style scoped>
.container {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  transform-origin: center;
  width: 1000px;
  margin: 0 auto 2em auto;
  padding: 1em 0.5em;
  display: flex;
  justify-content: center;
}

.indicator {
  position: absolute;
  top: 0;
  left: 0;
  width: 5px;
  height: 5px;
  background: #fff;
  border-radius: 100%;
  transition: all 1s cubic-bezier(0.075, 0.82, 0.165, 1);
}

.gallery {
  display: flex;
  justify-content: space-around;
  width: 100%;
  overflow: hidden;
}

.gallery-item {
  display: flex;
  justify-content: center;
  align-items: center;
  flex: 0 1 20px;
  height: 400px;
  margin: 0 5px;
  background: #000;
  overflow: hidden;
  transition: flex 1s cubic-bezier(0.075, 0.82, 0.165, 1);
}

.gallery-item img {
  width: 400px;
  height: 100%;
  object-fit: contain;
  transform: scale(2);
}
</style>
