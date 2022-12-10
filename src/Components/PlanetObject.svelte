<script>
	export let planet;
	export let ref;
</script>

<div
	class="planet-object"
	style="width: {planet.width}; height: {planet.height}; background: url({planet.image}) no-repeat center"
	bind:this={ref}
/>

<style>
	.planet-object {
		position: relative;
		background-size: cover;
		border-radius: 50%;
		z-index: 1;
	}
</style>
