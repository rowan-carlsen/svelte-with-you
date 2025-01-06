<script>
	import { slides } from './SlideContent.svelte';
	const { data } = $props();
	const index = $derived(parseInt(data.slide.slice(-1)));
	const length = $derived(Object.keys(slides).length);
</script>

{@render slides[data.slide]()}
<div id="button-holder">
	{#if index > 1}
		<a id="prev" href="/slide{index - 1}">Previous</a>
	{/if}
	{#if index < length}
		<a id="next" href="/slide{index + 1}">Next</a>
	{/if}
</div>

<style>
	#button-holder {
		grid-row: 5;
		grid-column: span 2;
		display: grid;
		grid-template-columns: 1fr 1fr;
		padding: 0.5em;
		justify-items: baseline;
	}
	#next {
		grid-column: 2;
		justify-self: end;
	}
	a {
		padding: 0.5em;
		border: 2px solid var(--secondary);
		border-radius: 0.5em;
	}
</style>
