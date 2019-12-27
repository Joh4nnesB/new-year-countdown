<template>
  <div id="app">
    <Countdown />

    <div class="credits">
      <div>Icons made by <a href="https://www.flaticon.com/authors/pongsakornred" title="pongsakornRed">pongsakornRed</a> from <a href="https://www.flaticon.com/" title="Flaticon">www.flaticon.com</a></div>
    </div>
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

.credits {
  margin-top: 1cm;
  color: grey;
  font-size: 0.6em;
}
</style>
