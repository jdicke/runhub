<script lang="ts">
    import { onMount } from "svelte";
  
    let elevation = 1000; // Initial altitude value
    let paceMinutes = 6;
    let paceSeconds = 0;
    let paces = [] as string[];
    const elevations = [10000, 9000, 8000, 7000, 6000, 5000, 4000, 3000, 2000, 1000, 0]
    let numbers = Array.from({ length: 11 }, (_, index) => index);
  
    // Function to calculate pace based on elevation
    function calculatePace() {
      const altitudeEffect: number = .001; // 0.1 seconds increase per 1000 feet
  
      paces = [];
      elevations.forEach(e => {
        const paceInSeconds: number = paceMinutes * 60 + e * altitudeEffect;
        let min = Math.floor(paceInSeconds / 60);
        let sec = Math.floor(paceInSeconds % 60);
        paces.push(formatPace(min, sec))
      })
    }
  
    // Function to handle pace format
    function formatPace(minutes: number, seconds: number): string {
      return `${String(minutes).padStart(2, "0")}:${String(seconds).padStart(2, "0")}`;
    }
  
    // Initialize with the default calculation
    onMount(() => {
      calculatePace();
    });
  </script>
  
  <main>
    <h1>Altitude Converter</h1>
  
    <label for="elevation">Elevation (feet):</label>
    <input type="number" bind:value={elevation}/>

    <label for="pace">Pace (min:sec):</label>
    <input type="number" bind:value={paceMinutes} on:input={calculatePace} />:
    <input type="number" bind:value={paceSeconds} on:input={calculatePace} />
  
    <div>
      <p>Pace at different altitudes:</p>
      <ul class="no-bullets">
        {#each numbers as number}
            <li>
                {elevations[number]} feet: {paces[number]}
            </li>
            {/each}
      </ul>
    </div>
  </main>
  
  <style>
    main {
      text-align: center;
      margin: 2rem;
    }
  
    input {
      margin-bottom: 1rem;
    }

    ul.no-bullets {
        list-style: none; /* Removes default list styling */
        padding: 0;
    }

    li {
        margin: 0.5rem 0;
    }
  </style>
  