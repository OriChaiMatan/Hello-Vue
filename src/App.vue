<template>
  <div>Hey Vue
    <CountDown :targetTime="Date.now() + 1000 * 60 * 0.5" />
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
};
</script>

<style scoped>
</style>
