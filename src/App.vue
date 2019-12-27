<template>
  <div id="app">
    <Countdown />
    <Credits />
  </div>
</template>

<script>
import Countdown from '@/components/Countdown.vue';
import Credits from '@/components/Credits.vue';
import BackgroundImage from '@/assets/background.jpg';

export default {
  name: 'app',
  components: {
    Countdown,
    Credits,
  },
  mounted() {
    document.body.style.backgroundImage = `url(${BackgroundImage})`;
  },
};
</script>

<style lang="scss">
// Import Raleway font from Google Fonts
@import url('https://fonts.googleapis.com/css?family=Lato:300,700&display=swap');

body {
  font-family: 'Lato', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  background-size: cover;
  background-repeat: no-repeat;
  height: 100vh;
  color: white;
  background-position: 50% 50%;
  text-align: center;
}

* {
  margin: 0;
  padding: 0;
}
</style>
