<template>
  <p>{{ end }}</p>
</template>

<script>
export default {
  name: "weather-footer",
  props: ["end"]
};
</script>

<style scoped>
p {
  font: 12px;
  font-family: sans-serif;
  color: white;
  background-color: black;
  padding: 0px;
}
</style>
