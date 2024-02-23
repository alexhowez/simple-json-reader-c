<script>
  import { onMount } from 'svelte';
  import { createEventDispatcher } from 'svelte';

	const dispatch = createEventDispatcher();

  let file;
  let errorMessage;

  function handleFileChange(event) {
    file = event.target.files[0];
    errorMessage = null;

    if (!file) return;

    const reader = new FileReader();
    reader.onload = (e) => {
      try {
        const data = JSON.parse(e.target.result);
        console.log("DATA 1", data)
        dispatch('jsonUpdate', {data});
      } catch (error) {
        errorMessage = 'Invalid JSON file';
      }
    };
    reader.readAsText(file);
  }
</script>

<input type="file" accept=".json" on:change={handleFileChange} />
{#if errorMessage}
  <p class="text-red-500">{errorMessage}</p>
{/if}

<button on:click={() => dispatch('jsonUpdate', null)}>Clear Data</button>

<style>
  input[type="file"] {
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
</style>
