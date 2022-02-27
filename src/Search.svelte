<script>
  import { key } from "./key.js";
  import { weatherList } from "./store.js";

  let cityName = "";

  function getFetchUrl(cityName) {
    return (
      "https://api.openweathermap.org/data/2.5/weather?units=metric&appid=" +
      key +
      "&q=" +
      cityName
    );
  }

  async function addWeatherInfo() {
    const res = await fetch(getFetchUrl(cityName));
    if (res.status === 404) {
      alert("Invalid City Name.");
    } else {
      weatherList.add(await res.json());
    }
    cityName = "";
  }
</script>

<div class="w3-card-4">
  <form class="w3-container">
    <p>
      <input
        type="text"
        class="w3-input w3-border w3-sand"
        placeholder="Enter City Name."
        bind:value={cityName}
      />
    </p>
    <p>
      <button
        type="button"
        class="w3-btn w3-center w3-highway-blue"
        style="width:100%"
        on:click={addWeatherInfo}>Add City</button
      >
    </p>
  </form>
</div>

<style type="text/scss">
</style>
