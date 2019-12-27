<template>
  <div>
    <h2>Time until {{ newYear }}:</h2>
    <div v-if="!completed">
      <CountdownElement v-show="showDays"    :value="remaining.days"    unit="Days"/>
      <CountdownElement v-show="showHours"   :value="remaining.hours"   unit="Hours"/>
      <CountdownElement v-show="showMinutes" :value="remaining.minutes" unit="Minutes"/>
      <CountdownElement v-show="showSeconds" :value="remaining.seconds" unit="Seconds"/>
    </div>
    <div v-else>Happy new year!</div>
  </div>
</template>

<script>
import time from '@/utils/time';
import CountdownElement from '@/components/CountdownElement.vue';

export default {
  components: {
    CountdownElement,
  },
  data: () => ({
    newYear: new Date().getUTCFullYear() + 1,
    updateInterval: 0,
    remaining: {
      days: 0,
      hours: 0,
      minutes: 0,
      seconds: 0,
    },
    completed: false,
  }),
  computed: {
    newYearDate() {
      return new Date(this.newYear, 0, 1, 0, 0, 0).getTime();
    },

    showDays() {
      return this.remaining.days > 0;
    },
    showHours() {
      return this.remaining.hours > 0 || this.showDays;
    },
    showMinutes() {
      return this.remaining.minutes > 0 || this.showHours;
    },
    showSeconds() {
      return this.remaining.seconds >= 0 || this.showMinutes;
    },
  },
  mounted() {
    const update = () => {
      // Get the current time in milliseconds
      const currentTime = new Date().getTime();
      // Calulate the remaining time between the current time and new year
      const remainingTime = this.newYearDate - currentTime;

      // If the remaining time is negative, the countdown was completed
      if (remainingTime < 0) {
        // If so, set "completed" to true and clear the interval
        this.completed = true;
        clearInterval(this.updateInterval);
        return;
      }

      // Calculate the remaining days, hours, minutes and seconds
      this.remaining.days = Math.floor(remainingTime / time.DAY_MS);

      this.remaining.hours = Math.floor(
        (remainingTime - this.remaining.days * time.DAY_MS)
        / time.HOUR_MS,
      );

      this.remaining.minutes = Math.floor(
        (remainingTime
          - this.remaining.days * time.DAY_MS
          - this.remaining.hours * time.HOUR_MS)
        / time.MINUTE_MS,
      );

      this.remaining.seconds = Math.floor(
        (remainingTime
          - this.remaining.days * time.DAY_MS
          - this.remaining.hours * time.HOUR_MS
          - this.remaining.minutes * time.MINUTE_MS)
        / time.SECOND_MS,
      );
    };

    // Invoke the update function every 500 ms
    update();
    this.updateInterval = setInterval(update, 500);
  },
  destroyed() {
    clearInterval(this.updateInterval);
  },
};
</script>

<style>

</style>
