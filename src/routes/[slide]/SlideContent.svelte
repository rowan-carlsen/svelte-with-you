<script module>
	const slides = { slide1, slide2, slide3, slide4 };
	export { slides };
	let hidden = $state(true);
	const reactExamples = [
		`const [thing, setThing] = useState(0);
function onclick() {
  setThing(t => t + 1);
}
...
<button onClick={onclick}>
Click Me
</button>`,
		`const [year, setYear] = useState(2014);
useEffect(() => {
  pingAPI(year)   
})`,
		`const [year, setYear] = useState(2014);
function handleChange(e) {
    setYear(e.currentTarget.value);
}
...
<input type="number" value={year}
onChange={handleChange} />`
	];
	const svelteExamples = [
		`let thing = $state(0);
function onclick() {
  thing++;
}
...
<button {onclick}>
Click Me
</button>`,
		`let year = $state(2014);
$effect(() => {
  pingAPI(year)
})`,
		`let year = $state(2014);
...
<input type="number" bind:value={year} />`
	];
	const svelte5 = [
		`//number.svelte.js

let number = $state(42);
let double = $derived(number * 2)
export {number, double};`,
		`{#snippet widget(word)}
  The word is {word}!
{/snippet}
...
//this could be:
//- the same file
//- a child component
//- something else entirely that imported the snippet!

{@render widget('ping')}
{@render widget('pong')}`
	];
</script>

{#snippet slide1()}
	<div class="header-area">
		<h1>Why Svelte?</h1>
		<h2>You'll see the difference...</h2>
	</div>
	<div class="box">
		<ul style="grid-column: span 4;">
			<li>Faster Apps/Pages with less code</li>
			<li>Deep Reactivity based on Signals</li>
			<li>Easy two-way binding for user inputs</li>
			<li>Decouples JavaScript from markup (unlike JSX)</li>
		</ul>
		<img class:hidden width="887" height="480" src="ob.jpg" alt="" />
		<img class:hidden width="887" height="480" src="nh.jpg" alt="" />
		<pre class:hidden><code>{reactExamples[0]}</code></pre>
		<pre class:hidden><code>{svelteExamples[0]}</code></pre>
		{#if hidden}
			<button id="show-btn" onclick={() => (hidden = false)}>OK, prove it!</button>
		{/if}
	</div>
{/snippet}

{#snippet slide2()}
	<div class="header-area">
		<h1>Why Svelte?</h1>
		<h2>You'll see the difference...</h2>
	</div>
	<div class="box">
		<img width="887" height="480" src="ob.jpg" alt="" />
		<img width="887" height="480" src="nh.jpg" alt="" />
		<pre class="horrified"><code>{reactExamples[1]}</code></pre>
		<pre><code>{svelteExamples[1]}</code></pre>
		<pre><code>{reactExamples[2]}</code></pre>
		<pre><code>{svelteExamples[2]}</code></pre>
	</div>
{/snippet}

{#snippet slide3()}
	<div class="header-area">
		<h1>What's New in Svelte 5?</h1>
		<h2>...and it's getting better, all the time!</h2>
	</div>
	<div class="box" style="gap: 2em; grid-template-rows: auto 1fr">
		<ul>
			<li>"Runes" allow for fine-grained reacivity - with opt-out</li>
			<li>More explicit syntax - easier to follow and compare to other frameworks</li>
			<li>Reactivity in plain .js/.ts files as well!</li>
			<li>"Snippets" allow for reusable HTML chunks inside components, or shared between them</li>
		</ul>
		<pre><code>{svelte5[0]}</code></pre>
		<pre style="grid-column: span 8; max-height:50vh"><code>{svelte5[1]}</code></pre>
	</div>
{/snippet}

{#snippet slide4()}
	<div class="header-area">
		<h1>OK, how do I start using it?</h1>
		<h2>There's nothing you and Svelte can't do...</h2>
	</div>
	<div class="box">
		<ul>
			<li><code>npx sv create</code></li>
			<li>TypeScript, JSDoc, or neither for type checking</li>
			<li>SvelteKit by default</li>
			<li>Can be used with Astro!</li>
			<li>Out of the box: transitions, crossfade, FLIP, tweening</li>
		</ul>
		<pre style="grid-row: span 2; max-height:60vh; grid-column: span 8;">
my-project/
├ src/
│ ├ lib/
│ │ ├ server/
│ │ │ └ [your server-only lib files]
│ │ └ [your lib files]
│ ├ params/
│ │ └ [your param matchers]
│ ├ routes/
│ │ └ [your routes]
│ ├ app.html
│ ├ error.html
│ ├ hooks.client.js
│ ├ hooks.server.js
│ └ service-worker.js
├ static/
│ └ [your static assets]
├ tests/
│ └ [your tests]
├ package.json
├ svelte.config.js
├ tsconfig.json
└ vite.config.js</pre>
	</div>
{/snippet}

<style>
	h2::before,
	h2::after {
		content: '\1F3B6';
	}
	h1,
	h2 {
		margin: 0;
	}
	.header-area {
		display: flex;
		flex-direction: column;
		gap: 1rem;
		grid-column: span 2;
		background: white;
		border: 2px solid var(--primary);
		border-width: 2px 0;
		padding: 1rem;
	}
	ul {
		grid-row: span 2;
		grid-column: span 4;
		font-size: 1.2rem;
		line-height: 2;
		background: white;
		align-self: flex-start;
		border: 2px solid var(--primary);
		padding: 0.5em;
		list-style-position: inside;
	}
	.box {
		grid-column: span 2;
		display: grid;
		grid-template-columns: repeat(12, 1fr);
		grid-template-rows: 1fr 1fr;
		grid-auto-flow: column;
		gap: 1em 0.5em;
		padding: 0 0.5rem;
		position: relative;
	}
	pre {
		grid-column: span 4;
		background-color: lightgrey;
		font-size: 1.2rem;
		padding: 0.5rem;
		border: 1px solid black;
		border-radius: 0.5rem;
		margin: 0;
		overflow: auto;
		max-height: 30vh;
		align-self: baseline;
		transition: opacity 0.5s;
	}
	img {
		width: 80%;
		height: auto;
		grid-column: span 4;
		margin: 0 auto;
		align-self: center;
		transition: opacity 0.5s;
	}
	.horrified {
		position: relative;
		padding-bottom: 2em;
		overflow: visible;
	}
	.horrified::after {
		position: absolute;
		bottom: 0;
		left: 1em;
		content: '\1F631';
		font-size: 2em;
	}
	.horrified::before {
		content: 'whoops, forgot dependency array...';
		position: absolute;
		top: calc(100% + 1px);
		left: 0;
		color: red;
		background-color: white;
	}
	.hidden {
		visibility: hidden;
		opacity: 0;
	}
	#show-btn {
		cursor: pointer;
		font-size: inherit;
		position: absolute;
		right: 0;
		top: 0;
		bottom: 0;
		left: 34%;
		width: max-content;
		height: max-content;
		margin: auto;
	}
</style>
