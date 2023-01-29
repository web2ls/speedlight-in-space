<script>
	import { fade } from 'svelte/transition';

	export let planets;
	export let selectedPlanet;
	export let changePlanet;

	let isVisible = false;

	function toggleList() {
		isVisible = !isVisible;
	}

	function onSelectPlanet(planetId) {
		toggleList();
		changePlanet(planetId);
	}
</script>

<div class="planet-selector">
	<div class="selected" on:click={toggleList} on:keypress={toggleList}>
		{selectedPlanet.label}
	</div>
	{#if isVisible}
		<ul class="planet-list" in:fade={{ delay: 100 }}>
			{#each planets as planet}
				<li
					class="planet-list__item"
					on:click={() => onSelectPlanet(planet.id)}
					on:keydown={() => onSelectPlanet(planet.id)}
				>
					{planet.label}
				</li>
			{/each}
		</ul>
	{/if}
</div>

<style>
	.planet-selector {
		position: relative;
		width: 100px;
		margin-right: 10px;
		cursor: pointer;
		z-index: 10;
		border: 2px solid var(--gray);
		border-radius: 10px;
	}

	.planet-selector:hover {
		color: var(--orange);
		border: 2px solid var(--base-color);
	}

	.selected {
		display: flex;
		justify-content: center;
		align-items: center;
		position: relative;
		padding: 0;
		text-align: center;
	}

	.planet-list {
		position: relative;
		padding: 3px 0;
		margin: 0;
		list-style-type: none;
		color: var(--base-color);
		text-align: center;
	}

	.planet-list__item {
		cursor: pointer;
	}

	.planet-list__item:hover {
		color: var(--orange);
	}

	@media only screen and (max-width: 1200px) and (orientation: landscape) {
		.planet-selector {
			width: 80px;
		}
	}
</style>
