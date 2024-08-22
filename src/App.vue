<template>
  <section class="app">
    <header class="app-header">
      <nav>
        <button v-on:click="route = 'Home'">Hello-Vue</button>
        <button v-on:click="route = 'ShowTime'">ShowTime</button>
        <button v-on:click="route = 'CountDown'">CountDown</button>
        <button v-on:click="route = 'WhoWatch'">WhoWatch</button>
        <button v-on:click="route = 'MouseMonitor'">MouseMonitor</button>
      </nav>
    </header>
    <div class="app-info">
      <CountDown
        v-if="route === 'CountDown'"
        :targetTime="Date.now() + 1000 * 60 * 0.25"
        @due="handleDueEvent"
      />
      <MouseMonitor v-if="route === 'MouseMonitor'" />
      <WhoWatch v-if="route === 'WhoWatch'" />
      <ShowTime v-if="route === 'ShowTime'" />
    </div>
  </section>
</template>

<script>
import CountDown from "./cmps/CountDown.vue";
import MouseMonitor from "./cmps/MouseMonitor.vue";
import ShowTime from "./cmps/ShowTime.vue";
import WhoWatch from "./cmps/WhoWatch.vue";
export default {
  components: {
    ShowTime,
    CountDown,
    WhoWatch,
    MouseMonitor,
  },
  data() {
    return {
      route: "ShowTime",
    };
  },
  methods: {
    handleDueEvent() {
      alert("Time is up!");
    },
  },
};
</script>

<style>
.app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

.app-header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  background-color: #0480c8;
  color: #fff;
  padding: 10px 0;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  z-index: 1000;
}

.app-header nav {
  display: flex;
  justify-content: center;
  gap: 15px;
}

.app-header button {
  background: none;
  border: none;
  color: #fff;
  font-size: 16px;
  cursor: pointer;
  padding: 10px 15px;
  transition: background-color 0.3s, color 0.3s;
}

.app-header button:hover {
  background-color: #555;
  color: #ffd700;
}

.app-info {
  margin-top: 50px; /* Adjust based on the height of the header */
  padding: 20px;
  flex: 1;
}
</style>
