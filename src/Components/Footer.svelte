<script>
	// TODO: Добавить время достижения в часах (например)
	// TODO: Как варинт добавить динамическое значение в зависимости от выбранной скорости
	// TODO: Отображать текущее значение скорости (света)
	// TODO: Как вариант отображать его динамически в зависимости от выбранного режима
	export let selectedPlanet;
	export let timeSpeed;
	export let selectedTimeSpeed;
	export let changeTimeSpeed;
</script>

<div class="footer">
	<div class="name">{selectedPlanet.label.toUpperCase()}</div>

	<div class="footer-item">
		<div class="header">Distance to</div>
		<div class="value">{selectedPlanet.distanceTo} km</div>
	</div>

	<div class="footer-item">
		<div class="header">Speed control</div>
		<div class="value time-speed">
			{#each timeSpeed as value}
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
		padding: 5px;
		border: 2px solid transparent;
		border-radius: 10px;
		cursor: pointer;
	}

	.time-speed__item.active {
		border: 2px solid var(--gray);
		border-radius: 10px;
	}

	.time-speed__item:hover {
		border: 2px solid var(--base-color);
		border-radius: 10px;
	}
</style>
