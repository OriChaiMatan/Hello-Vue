<template>
  <section class="count-down" :style="countdownStyle">
    <h1 class="title">Count Down</h1>
    <span>{{ formattedTime }}</span>
  </section>
</template>

<script>
export default {
  props: {
    targetTime: {
      type: Number,
      required: true
    }
  },
  data() {
    return {
      remainingTime: this.calculateRemainingTime()
    };
  },
  computed: {
    formattedTime() {
      const minutes = Math.floor((this.remainingTime % (1000 * 60 * 60)) / (1000 * 60));
      const seconds = Math.floor((this.remainingTime % (1000 * 60)) / 1000);

      return `${this.padTime(minutes)}:${this.padTime(seconds)}`;
    },
    countdownStyle() {
      return {
        color: this.remainingTime <= 10000 ? 'red' : 'black' // Changes to red in the last 10 seconds
      };
    }
  },
  created() {
    this.startCountdown();
  },
  methods: {
    calculateRemainingTime() {
      return Math.max(this.targetTime - Date.now(), 0);
    },
    startCountdown() {
      this.countdownInterval = setInterval(() => {
        this.remainingTime = this.calculateRemainingTime();

        if (this.remainingTime <= 0) {
          clearInterval(this.countdownInterval);
        }
      }, 1000);
    },
    padTime(value) {
      return String(value).padStart(2, '0');
    }
  },
  beforeDestroy() {
    clearInterval(this.countdownInterval);
  }
};
</script>

<style>
.count-down {
  font-size: 24px;
  font-weight: bold;
  text-align: center;
  background: #e6e6e9;
  padding: 10px;
  border-radius: 15px;
}
.title{
    color: #376ab2;
  }
</style>
