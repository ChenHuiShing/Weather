<template>
  <div id="app"></div>
</template>

<script>
export default {
  name: "App",
  mounted() {
    console.log("API KEY:", process.env.VUE_APP_WEATHER_KEY);
  }
};
</script>