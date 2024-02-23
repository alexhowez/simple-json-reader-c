<script>
  import initialData from './initialData.json';
  import Renderer from './_components/Renderer.svelte';
  import JsonSetter from './_components/JsonSetter.svelte';

  $: jsonData = initialData;

  function handleJsonChange(e) {
    jsonData = e?.detail?.data || [];
  }
</script>

<svelte:head>
  <title>Home</title>
  <meta content="Svelte demo app" />
</svelte:head>

<section>
  <div class="text-center border-lg bg-rose-100">
    <h1 class="font-bold text-2xl">JSON renderer</h1>
    <p class="font-bold">Quickly render json of 2 levels deep</p>
  </div>
  <JsonSetter  on:jsonUpdate={handleJsonChange} />
  <Renderer jsonData={jsonData} />
</section>
