<script>
	export let selectedPlanet;
</script>

<div class="footer">
	<div class="name">{selectedPlanet.label.toUpperCase()}</div>

	<div class="footer-item">
		<div class="header">Distance to</div>
		<div class="value">{selectedPlanet.distanceTo} km</div>
	</div>

	<div class="footer-item">
		<div class="header">Speed controls</div>
		<div class="value">1x 2x 5x</div>
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
</style>
