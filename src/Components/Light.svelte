<script>
	// TODO: Think about limit speed for the Moon object,
	// because it has low distance

	import { onMount } from 'svelte';

	export let distance;
	export let timeTo;
	export let selectedTimeSpeed;

	let ref;

	onMount(() => {
		const lightTransition = [
			{ transform: 'translateX(0)' },
			{ transform: `translateX(${distance}px)` },
			{ transform: 'translateX(0)' },
		];
		ref.animate(lightTransition, {
			duration: (timeTo * 1000) / selectedTimeSpeed,
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
