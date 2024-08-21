<template>
  <section class="show-time">
    <img :src="seasonImage" :alt="currentSeason" />
    <span>{{ currentTime }}</span>
  </section>
</template>

<script>
import springImage from '../assets/imgs/spring.png';
import summerImage from '../assets/imgs/summer.png';
import autumnImage from '../assets/imgs/autumn.png';
import winterImage from '../assets/imgs/winter.png';

export default {
  data() {
    return {
      currentTime: this.getCurrentTime(),
      currentSeason: this.getCurrentSeason(),
      seasonImages: {
        spring: springImage,
        summer: summerImage,
        autumn: autumnImage,
        winter: winterImage,
      },
    };
  },
  computed: {
    seasonImage() {
      return this.seasonImages[this.currentSeason];
    },
  },
  created() {
    this.startClock();
  },
  methods: {
    getCurrentTime() {
      const now = new Date();
      return now.toLocaleTimeString();
    },
    startClock() {
      setInterval(() => {
        this.currentTime = this.getCurrentTime();
      }, 1000);
    },
    getCurrentSeason() {
      const month = new Date().getMonth(); // Get the current month (0-11)
      if (month >= 2 && month <= 4) return 'spring';
      if (month >= 5 && month <= 7) return 'summer';
      if (month >= 8 && month <= 10) return 'autumn';
      return 'winter'; // Default for months 11, 0, 1
    },
  },
};
</script>

<style scoped>
.show-time {
  text-align: center;
}

img {
  width: 300px;
  height: auto;
  display: block;
  margin: 0 auto;
}

span {
  display: block;
  margin-top: 20px;
  font-size: 24px;
}
</style>
