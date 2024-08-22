<template>
  <div>Hey Vue
    <!-- <CountDown :targetTime="Date.now() + 1000 * 60 * 0.25" @due="handleDueEvent" /> -->
    <WhoWatch />
  </div>
</template>

<script>
import CountDown from './cmps/CountDown.vue';
import ShowTime from "./cmps/ShowTime.vue";
import WhoWatch from './cmps/WhoWatch.vue';
export default {
  components: {
    ShowTime,
    CountDown,
    WhoWatch,
  },
  methods: {
    handleDueEvent() {
      alert('Time is up!');
    }
  },
};
</script>

<style>
</style>
