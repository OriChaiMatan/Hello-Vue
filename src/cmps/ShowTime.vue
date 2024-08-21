<template>
  <section class="show-time" :class="{'dark-mode': isDarkMode}" @click="toggleBackground">
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
      isDarkMode: false,
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
      const month = new Date().getMonth(); 
      if (month >= 2 && month <= 4) return 'spring';
      if (month >= 5 && month <= 7) return 'summer';
      if (month >= 8 && month <= 10) return 'autumn';
      return 'winter';
    },
    toggleBackground() {
      this.isDarkMode = !this.isDarkMode; 
    },
  },
};
</script>

<style>
.show-time {
  text-align: center;
  padding: 20px;
  transition: background-color 0.3s ease;
  cursor: pointer;
  border-radius: 15px;
}

.show-time img {
  width: 300px;
  height: auto;
  display: block;
  margin: 0 auto;
}

.show-time span {
  display: block;
  margin-top: 20px;
  font-size: 24px;
}

.show-time.dark-mode {
  background-color: #85d0eb; 
  color: white; 
  border: 2px solid rgb(206, 206, 206);
}

.show-time {
  background-color: #fffefe; 
  border: 2px solid black;
}
</style>
