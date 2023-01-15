<script>
	import PlanetObject from '../Components/PlanetObject.svelte';
	import Light from '../Components/Light.svelte';
	import Footer from '../Components/Footer.svelte';
	import Hud from '../Components/HUD.svelte';

	import planetObjects from '../assets/data/objects.json';

	// TODO: возможно стоит вывести иконку с информацией по которой можно переходить на роут с информацией о планете

	const timeSpeed = [1, 10, 100];
	let lightSwitcher = false;
	let earthElement;
	let planetElement;
	let planets = [...planetObjects].slice(1);
	let selectedPlanet = planetObjects[0];
	let selectedTimeSpeed = 1;

	const changePlanet = (id) => {
		selectedPlanet = planetObjects.find((x) => x.id === id);
		planets = planetObjects.filter((x) => x.id !== id);

		if (lightSwitcher) {
			lightSwitcher = false;
			let timerId = setTimeout(() => {
				lightSwitcher = true;
				clearTimeout(timerId);
			}, 300);
		}
	};

	const calculateDistanceBetweenElements = () => {
		const earthRect = earthElement.getBoundingClientRect();
		const planetRect = planetElement.getBoundingClientRect();
		return planetRect.left - earthRect.right;
	};

	const onLightSwitcherClick = () => {
		lightSwitcher = !lightSwitcher;
	};

	const changeTimeSpeed = (value) => {
		selectedTimeSpeed = value;

		if (lightSwitcher) {
			lightSwitcher = false;
			let timerId = setTimeout(() => {
				lightSwitcher = true;
				clearTimeout(timerId);
			}, 300);
		}
	};
</script>

<div class="speed-container">
	<Hud
		{lightSwitcher}
		{onLightSwitcherClick}
		{planets}
		{selectedPlanet}
		{changePlanet}
	/>

	<div class="earth" bind:this={earthElement}>
		{#if lightSwitcher}
			<Light
				distance={calculateDistanceBetweenElements()}
				timeTo={selectedPlanet.timeTo}
				{selectedTimeSpeed}
			/>
		{/if}
	</div>

	<PlanetObject planet={selectedPlanet} bind:ref={planetElement} />

	<div class="blackground" />

	<Footer
		{selectedPlanet}
		{timeSpeed}
		{selectedTimeSpeed}
		{changeTimeSpeed}
	/>
</div>

<style>
	.speed-container {
		position: relative;
		display: flex;
		flex-direction: row;
		justify-content: space-around;
		align-items: center;
		width: 100%;
		height: 100vh;
		position: relative;
		background: url(background.jpg) no-repeat center;
		background-size: cover;
	}

	.earth {
		position: relative;
		display: flex;
		justify-content: flex-end;
		align-items: center;
		width: 100px;
		height: 100px;
		background: url(earth.png) no-repeat center;
		background-size: cover;
		border-radius: 50%;
		z-index: 10;
	}

	.blackground {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background: rgba(0, 0, 0, 0.4);
		z-index: 0;
	}
</style>
