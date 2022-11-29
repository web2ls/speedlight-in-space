<script>
	import PlanetObject from '../Components/PlanetObject.svelte';
	import LightSwitcher from '../Components/LightSwitcher.svelte';

	import planetObjects from '../assets/data/planetObjects.json';

	let lightSwitcher = false;
	let currentPlanet = planetObjects['moon'];

	const onSelectPlanet = (name) => {
		currentPlanet = planetObjects[name];
	};

	const onClickEarth = () => {
		console.log('yep');
	};

	const onLightSwitcherClick = () => {
		console.log('switcher click');
		lightSwitcher = !lightSwitcher;
	};
</script>

<div class="speed-container">
	<div class="object-selector">
		<select
			on:change={(event) => onSelectPlanet(event.currentTarget.value)}
		>
			<option value="moon">Moon</option>
			<option value="mars">Mars</option>
			<option value="jupiter">Jupiter</option>
		</select>
	</div>

	<LightSwitcher active={lightSwitcher} onClick={onLightSwitcherClick} />

	<div class="earth" on:click={onClickEarth} on:keypress={onClickEarth}>
		<div class="light" />
	</div>

	<PlanetObject planet={currentPlanet} />
</div>

<style>
	.speed-container {
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
		display: flex;
		justify-content: center;
		align-items: center;
		width: 50px;
		height: 50px;
		background: url(https://images.webfrontier.ru/image-from-rawpixel-id-6293608-png.png)
			no-repeat center;
		background-size: cover;
		border-radius: 50%;
	}

	.moon {
		width: 50px;
		height: 50px;
		background: url(https://images.webfrontier.ru/image-from-rawpixel-id-3474691-png.png)
			no-repeat center;
		background-size: cover;
		border-radius: 50%;
	}

	.light {
		width: 10px;
		height: 10px;
		background: transparent;
		background-size: cover;
		border-radius: 50%;
		transition: transform 1.28s linear;
	}

	.active-light {
		background: #fff;
	}

	.object-selector {
		position: absolute;
		top: 5px;
		left: 10px;
	}
</style>
