<template>
  <div id="app" :class="weatherPic">
    <div class="container">
      <!-- search bar -->
      <div class="select-box">
        <select @change="onSelectCity" class="city-select">
          <option disabled value="">請選擇台灣主要城市</option>
          <option value="Taipei">台北</option>
          <option value="New Taipei">新北</option>
          <option value="Taoyuan">桃園</option>
          <option value="Taichung">台中</option>
          <option value="Tainan">台南</option>
          <option value="Kaohsiung">高雄</option>
          <option value="Keelung">基隆</option>
          <option value="Hsinchu">新竹</option>
          <option value="Chiayi">嘉義</option>
          <option value="Changhua">彰化</option>
          <option value="Pingtung">屏東</option>
          <option value="Yilan">宜蘭</option>
          <option value="Hualien">花蓮</option>
          <option value="Taitung">台東</option>
          <option value="Nantou">南投</option>
          <option value="Yunlin">雲林</option>
          <option value="Miaoli">苗栗</option>
          <option value="Penghu">澎湖</option>
          <option value="Kinmen">金門</option>
          <option value="Lienchiang">連江</option>
        </select>
      </div>

      <div class="weather-wrapper">
        <!-- location & date info -->
        <div class="location-box">
          <div class="location">{{ selectedCity }}</div>
          <div class="date">{{ currentDate }}</div>
        </div>

        <!-- weather info -->
        <div class="weather-box">
          <div class="temperature"> {{  weatherTemperature }} °C</div>
          <div class="weather">{{ weather.weather[0].main }}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import dayjs from 'dayjs'
import advancedFormat from 'dayjs/plugin/advancedFormat'
dayjs.extend(advancedFormat)

export default {
  name: "App",
  data() {
    return {
      api_key: process.env.VUE_APP_WEATHER_KEY, //OpenWeatherMap API 的金鑰
      base_url: 'https://api.openweathermap.org/data/2.5/', //API 的基礎網址
      selectedCity: '', //select 選單選擇
      query: 'Taichung', //查詢用英文城市
      weather: {}, //用來儲存天氣資料的物件
      date: '' //用來儲存日期的字串
    }
  },
  computed:{
    currentDate() {
      // 使用 dayjs 套件取得現在的日期，並格式化成「月份 日 年份」的字串
      return dayjs().format('MMMM DD YYYY');
    },
    weatherTemperature() {
      // 取得天氣資料中的溫度，並四捨五入到整數
      return Math.round(Math.round(this.weather.main.temp));
    },
    weatherPic() {
      return this.weatherTemperature > 20 ? 'warm' : '';
    }
  },
  methods: {
    // select 選單選擇城市時
    onSelectCity(event) {
      // 直接將選擇的 value 指定給 weather.name
      const city = event.target.value;
      this.selectedCity = city;
      this.query = city;
      this.fetchWeather();
    },
    // 使用 fetch API 來取得天氣資料
    async fetchWeather() {
      const data = await fetch(`${this.base_url}weather?q=${this.query}&units=metric&APPID=${this.api_key}`)
      this.weather = await data.json()
      console.log( this.weather );
    }
  },
  created() {
        this.fetchWeather();
  }

}
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

.select-box .city-select{
  display: block;
  margin-top: 5px;
  margin-bottom: 10px;
  width: 100%; 
  padding:10px; 
  font-size: 16px;
  border-radius:10px;
  outline: none;
  background-color: hsl(0deg 0% 100% / 50%);
  transition: all 0.4s ease-in;
}

.select-box .city-select:focus {
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