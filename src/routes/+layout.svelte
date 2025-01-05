<script>
	let { children } = $props();
</script>

<main>
	{@render children()}
</main>

<style>
	main {
		height: 100%;
		overflow: hidden;
		display: grid;
		grid-template-rows: auto auto 1fr 1fr 2em;
		grid-template-columns: 1fr 1fr;
	}
</style>
