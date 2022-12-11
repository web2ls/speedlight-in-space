<script>
	import PlanetObject from '../Components/PlanetObject.svelte';
	import LightSwitcher from '../Components/LightSwitcher.svelte';
	import Light from '../Components/Light.svelte';

	import planetObjects from '../assets/data/objects.json';

	let lightSwitcher = false;
	let currentPlanet = planetObjects[0];
	let earthElement;
	let planetElement;

	const onSelectPlanet = (id) => {
		currentPlanet = planetObjects.find((x) => x.id === id);
	};

	const calculateDistanceBetweenElements = () => {
		const earthRect = earthElement.getBoundingClientRect();
		const planetRect = planetElement.getBoundingClientRect();
		return planetRect.left - earthRect.left;
	};

	const onLightSwitcherClick = () => {
		lightSwitcher = !lightSwitcher;
	};
</script>

<div class="speed-container">
	<div class="object-selector">
		<select
			on:change={(event) => onSelectPlanet(event.currentTarget.value)}
		>
			{#each planetObjects as planet}
				<option value={planet.id}>{planet.label}</option>
			{/each}
		</select>
	</div>

	<LightSwitcher active={lightSwitcher} onClick={onLightSwitcherClick} />

	<div class="earth" bind:this={earthElement}>
		{#if lightSwitcher}
			<Light distance={calculateDistanceBetweenElements()} />
		{/if}
	</div>

	<PlanetObject planet={currentPlanet} bind:ref={planetElement} />

	<div class="blackground" />
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
		background: url(https://images.webfrontier.ru/pexels-hristo-fidanov-1252890.jpg)
			no-repeat center;
		background-size: cover;
	}

	.earth {
		position: relative;
		display: flex;
		justify-content: center;
		align-items: center;
		width: 50px;
		height: 50px;
		background: url(https://images.webfrontier.ru/image-from-rawpixel-id-6293608-png.png)
			no-repeat center;
		background-size: cover;
		border-radius: 50%;
		z-index: 1;
	}

	.moon {
		width: 50px;
		height: 50px;
		background: url(https://images.webfrontier.ru/image-from-rawpixel-id-3474691-png.png)
			no-repeat center;
		background-size: cover;
		border-radius: 50%;
	}

	.object-selector {
		position: absolute;
		top: 5px;
		left: 10px;
		z-index: 1;
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
