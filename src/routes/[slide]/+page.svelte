<script>
	import { slides } from './SlideContent.svelte';
	const { data } = $props();
	const index = $derived(parseInt(data.slide.slice(-1)));
	const length = $derived(Object.keys(slides).length);
</script>

{@render slides[data.slide]()}
<div id="button-holder">
	{#if index > 1}
		<a href="/slide{index - 1}">Previous</a>
	{/if}
	{#if index < length}
		<a href="/slide{index + 1}">Next</a>
	{/if}
</div>

<style>
	#button-holder {
		grid-row: 5;
	}
</style>
