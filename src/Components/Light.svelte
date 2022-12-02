<script>
	import { fly } from 'svelte/transition';

	export let active;
	export let distance;

	let ref;

	const moveLightTo = () => {
		console.log(ref);
		ref.style.transform = `translateX(${distance}px)`;
	};

	// TODO: make animation as custom transition (https://css-tricks.com/making-your-first-custom-svelte-transition/)
</script>

{#if active}
	<div
		transition:fly={{ x: -200 }}
		class="light {active ? 'visible' : ''}"
		bind:this={ref}
	/>
{/if}

<style>
	.light {
		width: 10px;
		height: 10px;
		background: #fff;
		background-size: cover;
		border-radius: 50%;

		/* transition: transform 1.28s linear; */
	}

	.visible {
		background: #fff;
	}

	/* .active {
		transform: translateX(200px);
	} */

	/* Add animation based on transition */
</style>
