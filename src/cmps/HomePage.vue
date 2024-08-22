<template>
  <div class="home-page">
    <div class="home-content">
      <img src="../assets/imgs/vue-logo.png" alt="Vue Logo" class="vue-logo" />
      <h1>Welcome to My Vue Project</h1>
      <p>
        This is a basic Vue.js project designed to showcase various components and functionalities.
        Explore the features using the navigation menu at the top. Whether it's a countdown timer,
        a mouse monitor, or a demo of CRUDL whit list of users, you can see how Vue.js makes building interactive
        applications straightforward and enjoyable. Feel free to experiment and extend the project
        as you learn more about Vue.js.
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomePage'
};
</script>

<style scoped>
.home-page {
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  padding: 20px;
}

.home-content {
  max-width: 600px;
  background-color: #f5f5f5;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  padding: 20px;
}

.vue-logo {
  width: 100px;
  margin-bottom: 20px;
}

h1 {
  margin: 0;
  color: #42b983;
}

p {
  font-size: 18px;
  line-height: 1.6;
  color: #333;
}
</style>
