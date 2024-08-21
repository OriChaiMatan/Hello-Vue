<template>
  <section class="show-time">
    <span>{{ currentTime }}</span>
  </section>
</template>

<script>
export default {
  data() {
    return {
      currentTime: this.getCurrentTime(),
    };
  },
  created() {
    this.startClock();
  },
  methods: {
    getCurrentTime() {
      const now = new Date();
      return now.toLocaleTimeString(); // Formats time as HH:MM:SS
    },
    startClock() {
      setInterval(() => {
        this.currentTime = this.getCurrentTime();
      }, 1000); // Updates every second
    },
  },
};
</script>

<style scoped>
/* Add your styles here */
</style>
