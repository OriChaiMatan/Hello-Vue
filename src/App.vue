<template>
  <div>Hey Vue
    <CountDown :targetTime="Date.now() + 1000 * 60 * 0.25" @due="handleDueEvent" />
  </div>
</template>

<script>
import CountDown from './cmps/CountDown.vue';
import ShowTime from "./cmps/ShowTime.vue";
export default {
  components: {
    ShowTime,
    CountDown,
  },
  methods: {
    handleDueEvent() {
      alert('Time is up!');
    }
  },
};
</script>

<style scoped>
</style>
