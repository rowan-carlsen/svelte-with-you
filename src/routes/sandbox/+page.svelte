<script>
	let count = $state(1);
	let pokemon = $state('');
	let image = $state();

	let even = $derived(count % 2 === 0);

	$effect(async () => {
		const resp = await fetch(`https://pokeapi.co/api/v2/pokemon/${count}`);
		const json = await resp.json();
		pokemon = json.name;
		image = json.sprites.other['official-artwork'].front_default;
	});

	function onclick() {
		count++;
	}
</script>

<section>
	<button {onclick}>Increment Count</button>
	<div>
		Count: {count}
		<br />
		Even? {even}
		<br />
		Pokemon: {pokemon}
		<br />
		<img src={image} alt={pokemon} />
	</div>
</section>

<style>
	section {
		width: 100%;
		height: 100%;
		background: white;
		grid-row: span 4;
		grid-column: span 2;
		padding: 0.5rem;
	}
</style>
