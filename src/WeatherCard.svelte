<script>
  import { weatherList } from "./store.js";
  export let weather;
  export let index;

  let src =
    "http://openweathermap.org/img/w/" + weather.weather[0].icon + ".png";
  /* let duration = 1.5 * 1000; */

  /* let start = 0;
  let showDeleteSection = false; */

  function init() {
    start = new Date().getTime();
    showDeleteSection = false;
  }
  /* function openModal() {
    if (new Date().getTime() >= start + duration) {
      showDeleteSection = true;
    }
  }
  function closeModal() {
    start = 0;
    showDeleteSection = false;
  } */
  function remove() {
    weatherList.remove(index);
    closeModal();
  }

  let unix_timestamp = weather.dt;
  // Create a new JavaScript Date object based on the timestamp
  // multiplied by 1000 so that the argument is in milliseconds, not seconds.
  const today = new Date(unix_timestamp * 1000);
  /* var time =
  today.getHours() + ":" + today.getMinutes() + ":" + today.getSeconds(); */

  let currentTLocal = today.toUTCString();

  const celcius = Math.round(weather.main.temp);
</script>

<!-- <div class="card">
  <section on:mousedown={init} on:mouseup={openModal}>
    <h4><b>{weather.name}</b></h4>
    <img
      {src}
      alt={weather.weather[0].description}
      title={weather.weather[0].main}
    />
    <div class="container">
      {weather.main.temp}℃ / {weather.main.humidity}％ Humidity
    </div>
  </section>

  {#if showDeleteSection}
  <section>
    <button type="button" on:click={remove}>Remove</button>
    <button type="button" on:click={closeModal}>Cancel</button>
  </section>
  {/if}
</div> -->

<!-- Weather Card -->

<div class="w3-col s4 w3-center card-item" on:mousedown={init}>
  <!-- <div class="w3-display-container w3-text-white">
        <img {src} alt={weather.weather[0].description} />
        <div class="w3-xlarge w3-display-bottomleft w3-padding">
        {weather.weather[0].main}
        </div>
    </div> -->
  <!-- <div class="w3-row"> -->
  <div class="w3-center w3-margin-bottom">
    <h3>{weather.name}</h3>
    <p>{weather.sys.country}</p>
    <p>{celcius} ℃ / {weather.main.humidity}％ Humidity</p>
    <p>
      As of {currentTLocal}
    </p>
    <img {src} alt={weather.weather[0].description} style="width:80px" />
  </div>
  <div class="w3-center w3-margin">
    <button type="button" on:click={remove}>Remove</button>
    <!-- <button type="button" on:click={closeModal}>Cancel</button> -->
  </div>
  <!-- </div> -->
</div>

<style>
  p,
  h3 {
    color: white;
  }
</style>
