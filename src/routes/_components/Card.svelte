<script>
	import CardItem from './CardItem.svelte'
  export let item;
</script>

<div class="p-2 bg-rose-100">
  {#if item.children}
    <p class="font-semibold">{item?.title}</p>
    {#each Object.entries(item.children) as [key, value]}
      <CardItem key={key} value={value} />
    {/each}
  {:else}
    {#each Object.entries(item) as [key, value]}
      <CardItem key={key} value={value} />
    {/each}
  {/if}
</div>