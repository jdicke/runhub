<!-- ChatGPTPage.svelte -->

<script>
    import { onMount } from "svelte";
  
    let userQuery = "";
    let chatGPTResponse = "";
  
    async function generateWorkout() {
      // Call the API to get ChatGPT response
      try {
        // const response = await createChatGPTRequest(userQuery);
        const response = "Workout generates";
        chatGPTResponse = response;
      } catch (error) {
        console.error("Error fetching ChatGPT response:", error);
        chatGPTResponse = "An error occurred while generating the workout. Please try again later.";
      }
    }
  
    onMount(() => {
      // Initial request to ChatGPT
      generateWorkout();
    });
  </script>
  
  <main>
    <h1>Create a Workout Plan</h1>
  
    <label for="userQuery">Give me some details on a workout plan you would like me to create for you and I will try my best to create a great schedule:</label>
    <input type="text" id="userQuery" bind:value={userQuery} />
  
    <button on:click={generateWorkout}>Generate Workout</button>
  
    {#if chatGPTResponse}
      <div class="response">
        <strong>Workout Plan:</strong> {chatGPTResponse}
      </div>
    {/if}
  </main>
  
  <style>
    main {
      text-align: center;
      margin: 2rem;
    }
  
    label {
      display: block;
      margin-top: 0.5rem;
    }
  
    input {
      margin-bottom: 0.5rem;
    }
  
    button {
      margin-top: 1rem;
    }
  
    .response {
      margin-top: 1rem;
    }
  </style>
  