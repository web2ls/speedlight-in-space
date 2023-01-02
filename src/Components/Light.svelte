<script>
	import { onMount } from 'svelte';

	export let distance;

	let ref;
	let timing = 1.28;

	onMount(() => {
		// TODO: raname this animation
		const newspaperSpinning = [
			{ transform: 'translateX(0)' },
			{ transform: `translateX(${distance}px)` },
			{ transform: 'translateX(0)' },
		];
		ref.animate(newspaperSpinning, {
			duration: timing * 1000 * 2,
			iterations: Infinity,
		});
	});
</script>

<div class="light" bind:this={ref} />

<style>
	.light {
		position: relative;
		width: 10px;
		height: 10px;
		background: #fff;
		background-size: cover;
		border-radius: 50%;
		z-index: 10;
	}
</style>
