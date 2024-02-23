<script>
	import Card from './Card.svelte'
	export let jsonData
</script>


<section class="my-3 grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4">
  {#each jsonData as item}
    <Card item={item} />
  {/each}
</section>