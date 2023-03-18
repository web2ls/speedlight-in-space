<script>
	import FooterItem from './FooterItem.svelte';

	export let selectedPlanet;
	export let timeSpeedList;
	export let selectedTimeSpeed;
	export let changeTimeSpeed;
	export let timeTo;
	export let speedValue;

	let activeCarousel = 0;
	$: statsList = [
		{
			header: 'Distance to',
			value: `${selectedPlanet.distanceTo} km`,
		},
		{
			header: 'Time to',
			value: timeTo,
		},
		{
			header: 'Light speed',
			value: speedValue,
		},
	];

	const next = () => {
		if (activeCarousel + 1 > statsList.length - 1) activeCarousel = 0;
		else activeCarousel += 1;
	};

	const prev = () => {
		if (activeCarousel - 1 < 0) activeCarousel = statsList.length - 1;
		else activeCarousel -= 1;
	};
</script>

<div class="footer">
	<div class="name">{selectedPlanet.label.toUpperCase()}</div>

	<div class="desktop-stats">
		<FooterItem
			header="Distance to"
			value="{selectedPlanet.distanceTo} km"
		/>

		<FooterItem header="Time to" value={timeTo} />

		<FooterItem header="Light speed" value={speedValue} />
	</div>

	<div class="tablet-stats">
		<div class="slider-stats" on:click={prev} on:keydown={prev}>
			<svg viewBox="0 0 24 24"
				><path
					d="M12 2a10 10 0 1 0 10 10A10.011 10.011 0 0 0 12 2zm0 18a8 8 0 1 1 8-8 8.009 8.009 0 0 1-8 8z"
				/><path
					d="M13.293 7.293 8.586 12l4.707 4.707 1.414-1.414L11.414 12l3.293-3.293-1.414-1.414z"
				/></svg
			>
		</div>
		<div>
			<svelte:component
				this={FooterItem}
				header={statsList[activeCarousel].header}
				value={statsList[activeCarousel].value}
			/>
		</div>
		<div class="slider-stats" on:click={next} on:keydown={next}>
			<svg viewBox="0 0 24 24"
				><path
					d="M12 2a10 10 0 1 0 10 10A10.011 10.011 0 0 0 12 2zm0 18a8 8 0 1 1 8-8 8.009 8.009 0 0 1-8 8z"
				/><path
					d="M9.293 8.707 12.586 12l-3.293 3.293 1.414 1.414L15.414 12l-4.707-4.707-1.414 1.414z"
				/></svg
			>
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
		flex-shrink: 0;
		font-size: 24px;
		font-weight: 700;
		color: var(--orange);
		letter-spacing: 1px;
		border-right: 1px solid var(--orange);
		line-height: 50px;
		padding-right: 10px;
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

	.desktop-stats,
	.tablet-stats {
		flex-grow: 1;
		display: flex;
		justify-content: space-around;
		align-items: center;
	}

	.tablet-stats {
		display: none;
	}

	.slider-stats {
		width: 30px;
		height: 30px;
		cursor: pointer;
	}

	.slider-stats svg {
		fill: var(--base-color);
	}

	.slider-stats:hover svg {
		fill: var(--orange);
	}

	@media only screen and (max-width: 1200px) {
		.desktop-stats {
			display: none;
		}

		.tablet-stats {
			display: flex;
		}
	}

	@media only screen and (max-width: 962px) {
		.footer {
			height: 50px;
		}

		.name {
			font-size: 16px;
		}

		.header {
			font-size: 14px;
		}

		.value {
			font-size: 14px;
		}
	}

	@media only screen and (max-width: 420px) and (orientation: portrait) {
		.tablet-stats {
			display: none;
		}
	}
</style>
