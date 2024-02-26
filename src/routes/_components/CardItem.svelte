<script>
  import { copy } from 'svelte-copy';

  export let key;
  export let value;
</script>

<div class="my-2 flex justify-between items-center">
  <p>{key}: {value}</p>
  <button class="px-3 py-1 bg-red-500 text-white font-medium rounded-sm hover:bg-blue-700" 
  use:copy={value}
  >COPY</button>
</div>
