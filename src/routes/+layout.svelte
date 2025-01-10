<script>
	import { onNavigate } from '$app/navigation';
	let { children } = $props();
	onNavigate(() => console.log('navigating', new Date()));
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
		position: relative;
		overflow: hidden;
		display: grid;
		grid-template-rows: auto auto 1fr 2em;
		max-height: 100%;
		grid-template-columns: 1fr 1fr;
	}
	main::after {
		content: '';
		position: absolute;
		top: 0;
		left: 0;
		width: calc(100% + 80px);
		height: calc(100% + 80px);
		z-index: -2;
		background-image: linear-gradient(to bottom, #fff 22%, transparent 22%),
			linear-gradient(to right, #fff 25%, transparent 25%),
			linear-gradient(to left, #fff 25%, transparent 25%),
			linear-gradient(
				150deg,
				transparent 32%,
				#dedede calc(32% + 1px),
				transparent calc(32% + 2px)
			),
			linear-gradient(
				210deg,
				transparent 32%,
				#dedede calc(32% + 1px),
				transparent calc(32% + 2px)
			),
			linear-gradient(335deg, #fff 27%, transparent 27%),
			linear-gradient(25deg, #fff 27%, transparent 27%),
			conic-gradient(
				#fefefe 60deg,
				#dadada 60deg,
				#dadada 180deg,
				#ececec 180deg,
				#ececec 300deg,
				#fff 300deg
			);
		background-size: 80px 80px;
		animation: fun 2s infinite;
		background-position: 0 0;
	}
	@keyframes fun {
		to {
			transform: translate(-80px, -80px);
		}
	}
</style>
