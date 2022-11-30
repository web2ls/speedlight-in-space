<script>
	export let active;
	export let ref;
</script>

<div class="light {active ? 'active' : ''}" bind:this={ref} />

<style>
	.light {
		width: 10px;
		height: 10px;
		background: #fff;
		background-size: cover;
		border-radius: 50%;
		transition: transform 1.28s linear;
	}

	.active {
		transform: translateX(200px);
	}

	/* Add animation based on transition */
</style>
