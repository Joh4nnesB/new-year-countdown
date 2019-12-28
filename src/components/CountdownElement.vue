<template>
  <div class="container">
    <div class="value">{{ value }}</div>
    <div class="unit">{{ unit }}</div>
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

<style lang="scss" scoped>
.container {
  $container-size: 15vw;
  width: $container-size;
  height: $container-size;

  // If there exists a better solution, please open an issue or a pull request
  @media only screen and (max-width: 800px) {
    width: 3.5cm;
    height: 3.5cm;
  }

  display: inline-grid;
  grid-template-rows: auto 1.5em;

  background-color: #2980b9;
  margin: 2mm;
  padding: 2vmin;

  .value {
    font-size: 8vw;
    @media only screen and (max-width: 800px) {
      font-size: 5.5em;
    }

    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;

    background-color: #3498db;
  }

  .unit {
    margin-top: 1vmin;

    text-transform: uppercase;
    text-align: center;
    font-weight: 700;
  }
}
</style>
