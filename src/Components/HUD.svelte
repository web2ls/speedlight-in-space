<script>
	import PlanetSelector from './PlanetSelector.svelte';
	import LightSwitcher from './LightSwitcher.svelte';

	export let lightSwitcher;
	export let onLightSwitcherClick;
	export let planets;
	export let selectedPlanet;
	export let changePlanet;
</script>

<div class="hud">
	<PlanetSelector {planets} {selectedPlanet} {changePlanet} />
	<LightSwitcher active={lightSwitcher} onClick={onLightSwitcherClick} />
</div>

<style>
	.hud {
		position: absolute;
		top: 5px;
		left: 10px;
		z-index: 10;
		display: flex;
		padding: 10px;
		border: 1px solid var(--gray);
		border-radius: 10px;
	}

	@media only screen and (max-width: 1200px) {
		.hud {
			left: 50%;
			transform: translateX(-50%);
		}

		@media only screen and (max-width: 1200px) {
			.hud {
				padding: 5px;
			}
		}
	}
</style>
