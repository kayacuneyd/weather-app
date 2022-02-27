<script>
  import { weatherList } from "./store.js";
  import WeatherCard from "./WeatherCard.svelte";
</script>

<div class="w3-row-padding">
  {#each $weatherList as weather, index}
    <WeatherCard {weather} {index} />
  {/each}
</div>
