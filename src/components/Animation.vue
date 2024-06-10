<template>
  <div id="image-track" data-mouse-down-at="0" data-prev-percentage="0">
    <img
      v-for="(image, index) in images"
      :key="index"
      :src="image"
      :class="{ image: true, selected: index === selectedIndex }"
      @click="toggleZoom(index)"
      draggable="false"
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      images: [
        require("../assets/deepscan.png"),
        require("../assets/purevision.png"),
        require("../assets/isaac.png"),
        require("../assets/tirescope.png"),
        require("../assets/hub.png"),
      ],
      selectedIndex: null,
    };
  },
  methods: {
    toggleZoom(index) {
      if (this.selectedIndex === index) {
        // Eğer zaten seçili olan resme tıklanırsa, zoom'u kapat
        this.selectedIndex = null;
      } else {
        // Aksi halde tıklanan resmi zoom yap
        this.selectedIndex = index;
      }
    },
  },
  mounted() {
    const track = document.getElementById("image-track");

    let nextPercentage = 0;

    const handleMouseDown = (e) => {
      track.dataset.mouseDownAt = e.clientX;
    };

    const handleMouseMove = (e) => {
      if (track.dataset.mouseDownAt === "0") return;

      const mouseDelta = parseFloat(track.dataset.mouseDownAt) - e.clientX;
      const maxDelta = window.innerWidth / 2;

      const percentage = (mouseDelta / maxDelta) * -100;
      nextPercentage = Math.max(
        Math.min(parseFloat(track.dataset.prevPercentage) + percentage, 0),
        -100
      );

      track.dataset.percentage = nextPercentage;
      track.style.transform = `translate(${nextPercentage}%, -50%)`;

      for (const image of track.getElementsByClassName("image")) {
        image.style.objectPosition = `${100 + nextPercentage}% center`;
      }
    };

    const handleMouseUp = () => {
      track.dataset.mouseDownAt = "0";
      track.dataset.prevPercentage = nextPercentage;
    };

    window.addEventListener("mousedown", handleMouseDown);
    window.addEventListener("mousemove", handleMouseMove);
    window.addEventListener("mouseup", handleMouseUp);

    // Touch event handlers for mobile devices
    window.addEventListener("touchstart", (e) => handleMouseDown(e.touches[0]));
    window.addEventListener("touchmove", (e) => handleMouseMove(e.touches[0]));
    window.addEventListener("touchend", handleMouseUp);
  },
};
</script>

<style>
#image-track > .image {
  width: 40vmin; /* Normal boyut */
  height: 56vmin; /* Normal boyut */
  object-fit: cover;
  object-position: center center;
  transition: width 0.2s, height 0.2s; /* Geçiş efekti */
}

#image-track > .image.selected {
  width: 60vmin;
  height: 84vmin;
  z-index: 1;
}
#image-track {
  display: flex;
  gap: 4vmin;
  position: absolute;
  align-items: center;
  left: 50%;
  top: 50%;
  transform: translate(0%, -50%);
  transition: transform 0.5s cubic-bezier(0.075, 0.82, 0.165, 1);
  cursor: pointer;
}
</style>
