<template>
  <div>
    <div>{{ value }}</div>
    <div>{{ unit }}</div>
  </div>
</template>

<script>
export default {
  props: {
    value: Number,
    unit: String,
  },
};
</script>

<style>

</style>
