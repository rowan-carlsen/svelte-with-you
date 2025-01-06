<script>
	let { children } = $props();
</script>

<svelte:head>
	<title>Svelte With You!</title>
</svelte:head>
<main>
	{@render children()}
</main>

<style>
	main {
		height: 100%;
		overflow: hidden;
		display: grid;
		grid-template-rows: auto auto 1fr 2em;
		max-height: 100%;
		grid-template-columns: 1fr 1fr;
	}
</style>
