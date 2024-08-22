<template>
  <div class="coords-display">
    <p>X: {{ x }} | Y: {{ y }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      x: 0,
      y: 0,
    };
  },
  mounted() {
    document.body.addEventListener('mousemove', this.updateCoords);
  },
  beforeDestroy() {
    document.body.removeEventListener('mousemove', this.updateCoords);
  },
  methods: {
    updateCoords(event) {
      this.x = event.clientX;
      this.y = event.clientY;
    },
  },
};
</script>

<style scoped>
.coords-display {
  background: rgba(48, 225, 202, 0.7);
  color: white;
  padding: 100px;
  font-size: 20px;
  z-index: 1000;
  border-top: 1px solid #ccc;
  border-radius: 15px;
}
</style>
