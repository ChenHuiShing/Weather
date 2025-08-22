<template>
  <div id="app">
    <div class="container">
      <!-- search bar -->
      <div class="search-box">
        <input type="text" placeholder="Search for a city..." class="search-bar" />
      </div>

      <div class="weather-wrapper">
        <!-- location & date info -->
        <div class="location-box">
          <div class="location">Taichung</div>
          <div class="date">Octorber 8th 2020</div>
        </div>

        <!-- weather info -->
        <div class="weather-box">
          <div class="temperature">26°C</div>
          <div class="weather">Cloud</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App"
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  background-image: url('./assets/cold-bg.jpg');
  background-size: cover; /* cover the entire viewport */
  background-position: 50%;
  transition: 0.5s;
}

#app.warm {
  background-image: url('./assets/warm-bg.jpg');
}

.container {
  height: 100vh;
  padding: 25px;
  background-image: linear-gradient(
    to bottom,
    rgba(0, 0, 0, 0.25),
    rgba(0, 0, 0, 0.75)
  )
}

.search-box {
  width: 100%;
  margin-bottom: 35px;
}

.search-box .search-bar {
  display: block;
  width: 100%;
  padding: 15px;
  transition: all 0.4s ease-in;
  border-radius: 15px;
  font-size: 20px;
  border: none;
  outline: none;
  background: none;
  background-color: hsla(0,0%,100%,.5);
}

.search-box .search-bar:focus {
  background-color: rgba(255, 255, 255, 0.75);
  box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
}

.location-box .location {
  font-family: 'Lucida Sans';
  color: #fff;
  font-size: 32px;
  font-weight: 500;
  text-align: center;
  text-shadow: 5px 2px rgba(0, 0, 0, 0.25)
}

.location-box .date {
  margin: 5px;
  color: #fff;
  font-size: 20px;
  font-weight: 300;
  text-align: center;
  font-style: italic;
}

.weather-box {
  text-align: center;
  margin-top: 15px;
}

.weather-box .temperature {
  display: inline-block;
  padding: 10px 25px;
  color: #fff;
  font-size: 92px;
  font-weight: 900;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.25);
  border-radius: 10px;
  box-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}

.weather-box .weather {
  margin-top: 20px;
  font-size: 42px;
  color: #ffffff;
  font-weight: 700;
  font-style: italic;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}

</style>