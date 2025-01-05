<script module>
	const slides = { slide1, slide2, slide3 };
	export { slides };
</script>

{#snippet slide1()}
	<h1>Why Svelte?</h1>
	<h2>You'll see the difference...</h2>
	<ul>
		<li>Faster Apps/Pages with less code</li>
		<li>Deep Reactivity based on Signals</li>
		<li>Easy two-way binding for user inputs</li>
		<li>Decouples JavaScript from markup (unlike JSX)</li>
	</ul>
	<pre>
		let thing = $state(0);
		thing++;
	</pre>
	<pre>
		const [thing, setThing] = useState(0);
		setThing(t => t + 1);
	</pre>
{/snippet}

{#snippet slide2()}
	<h1>What's New in Svelte 5?</h1>
	<h2>...and it's getting better, all the time!</h2>
	<ul>
		<li>"Runes" allow for fine-grained reacivity - with opt-out</li>
		<li>More explicit syntax - easier to follow and compare to other frameworks</li>
		<li>Reactivity in plain .js/.ts files as well!</li>
		<li>"Snippets" allow for reusable HTML chunks inside components, or shared between them</li>
	</ul>
{/snippet}

{#snippet slide3()}
	<h1>OK, how do I start using it?</h1>
	<h2>There's nothing you and Svelte can't do...</h2>
	<ul>
		<li><code>npx sv create</code></li>
		<li>TypeScript, JSDoc, or neither for type checking</li>
		<li>SvelteKit by default</li>
		<li>Can be used with Astro!</li>
		<li>Out of the box: transitions, crossfade, FLIP, tweening</li>
	</ul>
{/snippet}

<style>
	h2::before,
	h2::after {
		content: '\1F3B6';
	}
	h1,
	h2 {
		grid-column: span 2;
		margin: 0.5rem 0;
	}
	ul {
		grid-row: span 2;
	}
</style>
