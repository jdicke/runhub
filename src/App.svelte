<script lang="ts">
  import raceLogo from "./assets/race.svg";
  import mountainLogo from "./assets/moutain.svg";
  import shoeLogo from "./assets/shoe.svg";
  import workoutLogo from "./assets/workout.svg";
  import Counter from "./lib/Counter.svelte";
  import Altitude from "./lib/Altitude.svelte";
  import Shoe from "./lib/Shoe.svelte";
  import Race from "./lib/Race.svelte";
  import Workout from "./lib/Workout.svelte";
  let showAltitude = false;
  function toggleAltitudeDiv() {
    showAltitude = !showAltitude;
    showShoe = false;
    showWorkout = false;
    showRace = false;
  }
  let showShoe = false;
  function toggleShoe() {
    showShoe = !showShoe;
    showAltitude = false;
    showWorkout = false;
    showRace = false;
  }
  let showWorkout = false;
  function toggleWorkout() {
    showWorkout = !showWorkout;
    showShoe = false;
    showAltitude = false;
    showRace = false;
  }
  let showRace = false;
  function toggleRace() {
    showRace = !showRace;
    showShoe = false;
    showAltitude = false;
    showWorkout = false;
  }
</script>

<main>
  <div>
    <img
      src={mountainLogo}
      class="logo"
      alt="Altitude Converter"
      on:click={toggleAltitudeDiv}
    />

    <img
      src={shoeLogo}
      class="logo shoe"
      alt="Shoe Matrix"
      on:click={toggleShoe}
    />

    <img
      src={workoutLogo}
      class="logo workout"
      alt="Workout Maker"
      on:click={toggleWorkout}
    />

    <img
      src={raceLogo}
      class="logo medal"
      alt="Race Predictor"
      on:click={toggleRace}
    />
  </div>
  {#if showAltitude}
    <div>
      <Altitude />
    </div>
  {/if}
  {#if showShoe}
    <div>
      <Shoe />
    </div>
  {/if}
  {#if showRace}
    <div>
      <Race />
    </div>
  {/if}
  {#if showWorkout}
    <div>
      <Workout />
    </div>
  {/if}

  <h1 class="title">runhub</h1>

  <div class="card">
    <Counter />
  </div>

  <p>Everything you need for your running journey. All in one place.</p>

  <p class="read-the-docs">
    Click on icons above to navigate your way through the website.
  </p>
</main>

<style>
  .title:hover {
    filter: drop-shadow(0 0 1em #646cffaa);
  }
  .logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
    transition: filter 300ms;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
    cursor: pointer;
  }
  .logo.shoe:hover {
    filter: drop-shadow(0 0 2em #777777aa);
  }
  .logo.workout:hover {
    filter: drop-shadow(0 0 2em #8e08a0aa);
  }
  .logo.medal:hover {
    filter: drop-shadow(0 0 2em #ebdb06aa);
  }
  .read-the-docs {
    color: #888;
  }
</style>
