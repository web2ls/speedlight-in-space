<script>
	// TODO: разделить футер на десктоп и мобильную версию
	// TODO убрать компонент FooterItem и заменить его статикой
	import FooterItem from './FooterItem.svelte';

	const SECONDS_IN_MINUTE = 60;
	export let selectedPlanet;
	export let timeSpeedList;
	export let selectedTimeSpeed;
	export let changeTimeSpeed;
	export let timeTo;

	const formatSpeedValue = (value) => {
		let result = '';
		let counter = 0;

		for (let i = value.length - 1; i >= 0; i--) {
			if (counter < 3) {
				result = value[i] + result;
				counter++;
			} else {
				counter = 1;
				result = ' ' + result;
				result = value[i] + result;
			}
		}

		return result;
	};

	const calculateTimeTo = () => {
		let timeTo = null;

		if (selectedTimeSpeed === 1) {
			timeTo = `${(selectedPlanet.timeTo / SECONDS_IN_MINUTE).toFixed(
				2
			)} minutes`;
		} else {
			timeTo = `${(
				selectedPlanet.timeTo /
				SECONDS_IN_MINUTE /
				selectedTimeSpeed
			).toFixed(2)} minutes`;
		}

		return timeTo;
	};
</script>

<div class="footer">
	<div class="name">{selectedPlanet.label.toUpperCase()}</div>

	<FooterItem header="Distance to" value="{selectedPlanet.distanceTo} km" />

	<FooterItem header="Time to" value={timeTo} />

	<div class="footer-item">
		<div class="header">Time to</div>
		<div class="value">
			{#if selectedTimeSpeed === 1}
				{(selectedPlanet.timeTo / SECONDS_IN_MINUTE).toFixed(2)} minutes
			{:else}
				{(
					selectedPlanet.timeTo /
					SECONDS_IN_MINUTE /
					selectedTimeSpeed
				).toFixed(2)} minutes
			{/if}
		</div>
	</div>

	<div class="footer-item">
		<div class="header">Light speed</div>
		<div class="value">
			{formatSpeedValue((300000 * selectedTimeSpeed).toString())} km/s
		</div>
	</div>

	<div class="footer-item">
		<div class="header">Speed control</div>
		<div class="value time-speed">
			{#each timeSpeedList as value}
				<div
					on:click={() => changeTimeSpeed(value)}
					on:keydown={() => changeTimeSpeed(value)}
					class="time-speed__item {selectedTimeSpeed === value
						? 'active'
						: ''}"
				>
					{value}x
				</div>
			{/each}
		</div>
	</div>
</div>

<style>
	.footer {
		position: fixed;
		left: 0;
		bottom: 0;
		width: 100%;
		height: 83px;
		display: flex;
		flex-direction: row;
		justify-content: space-around;
		align-items: center;
		padding: 5px;
		background: #272727;
		z-index: 10;
		overflow: hidden;
	}

	.footer-item {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	.name {
		font-size: 24px;
		font-weight: 700;
		color: var(--orange);
		letter-spacing: 1px;
	}

	.header {
		font-size: 16px;
		color: var(--orange);
		font-weight: 700;
		letter-spacing: 1px;
	}

	.value {
		font-size: 16px;
		font-weight: 400;
		color: var(--base-color);
		letter-spacing: 3px;
	}

	.value.time-speed {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
	}

	.time-speed__item {
		margin-right: 10px;
		padding: 1px 5px;
		border: 2px solid transparent;
		border-radius: 10px;
		cursor: pointer;
		transition: all 0.3s;
	}

	.time-speed__item.active {
		border: 2px solid var(--gray);
		border-radius: 10px;
	}

	.time-speed__item:hover {
		border: 2px solid var(--base-color);
		border-radius: 10px;
	}

	@media only screen and (max-width: 768px) {
	}
</style>
