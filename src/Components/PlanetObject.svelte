<script>
	export let planet;
	export let ref;
</script>

<div
	class="planet-object"
	style="width: {planet.width}px; height: {planet.height}px; background: url({planet.image}.png) no-repeat center"
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
