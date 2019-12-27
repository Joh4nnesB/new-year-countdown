<template>
  <div id="app">
    <Countdown />
  </div>
</template>

<script>
import Countdown from '@/components/Countdown.vue';

export default {
  name: 'app',
  components: {
    Countdown,
  },
};
</script>

<style lang="scss">
// Import Raleway font from Google Fonts
@import url('https://fonts.googleapis.com/css?family=Raleway:400,700&display=swap');

body {
  font-family: 'Raleway', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
