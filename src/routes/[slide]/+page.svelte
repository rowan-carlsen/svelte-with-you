<script>
	import { slides } from './SlideContent.svelte';
	const { data } = $props();
	const index = $derived(parseInt(data.slide.slice(-1)));
	const length = $derived(Object.keys(slides).length);
</script>

{@render slides[data.slide]()}
<div id="button-holder">
	<a id="prev" href={index <= 1 ? '/' : `/slide${index - 1}`}>Previous</a>
	<a id="next" href={index >= length ? '/sandbox' : `/slide${index + 1}`}>Next</a>
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
</style>
