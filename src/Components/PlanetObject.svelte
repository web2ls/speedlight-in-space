<script>
	export let planet;
</script>

<div
	class="planet-object"
	style="width: {planet.width}; height: {planet.height}; background: url({planet.image}) no-repeat center"
/>

<style>
	.planet-object {
		background-size: cover;
		border-radius: 50%;
	}
</style>
