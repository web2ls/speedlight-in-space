<script>
	import PlanetObject from '../Components/PlanetObject.svelte';
	import LightSwitcher from '../Components/LightSwitcher.svelte';
	import Light from '../Components/Light.svelte';
	import Hud from '../Components/Hud.svelte';

	import planetObjects from '../assets/data/objects.json';

	// TODO: добавить контроль светом в виде ЧБ иконки с подсветкой
	// TODO: возможно стоит вывести иконку с информацией по которой можно переходить на роут с информацией о планете

	let lightSwitcher = false;
	let currentPlanet = planetObjects[0];
	let earthElement;
	let planetElement;

	const onSelectPlanet = (id) => {
		if (lightSwitcher) {
			lightSwitcher = false;
		}

		currentPlanet = planetObjects.find((x) => x.id === id);
	};

	const calculateDistanceBetweenElements = () => {
		const earthRect = earthElement.getBoundingClientRect();
		const planetRect = planetElement.getBoundingClientRect();
		return planetRect.left - earthRect.right;
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
			<Light
				distance={calculateDistanceBetweenElements()}
				timeTo={currentPlanet.timeTo}
			/>
		{/if}
	</div>

	<PlanetObject planet={currentPlanet} bind:ref={planetElement} />

	<div class="blackground" />

	<Hud {currentPlanet} />
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
