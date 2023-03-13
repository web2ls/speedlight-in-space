<script>
	export let planet;
	export let ref;
</script>

<div
	class="planet-object {planet.id}"
	style="background: url({planet.image}.png) no-repeat center; background-size: cover"
	bind:this={ref}
/>

<style>
	.planet-object {
		position: relative;
		background-size: cover;
		border-radius: 50%;
		z-index: 1;
	}

	.moon {
		width: 25px;
		height: 25px;
	}

	.mercury {
		width: 33px;
		height: 33px;
	}

	.venus {
		width: 90px;
		height: 90px;
	}

	.mars {
		width: 50px;
		height: 50px;
	}

	.jupiter {
		width: 300px;
		height: 300px;
	}

	.saturn {
		width: 640px;
		height: 470px;
	}

	.uranus {
		width: 180px;
		height: 180px;
	}

	.neptune {
		width: 150px;
		height: 150px;
	}

	.pluto {
		width: 25px;
		height: 25px;
	}

	@media only screen and (max-width: 1200px) {
		.moon {
			width: 25px;
			height: 25px;
		}

		.mercury {
			width: 33px;
			height: 33px;
		}

		.venus {
			width: 50px;
			height: 50px;
		}

		.mars {
			width: 40px;
			height: 40px;
		}

		.jupiter {
			width: 110px;
			height: 110px;
		}

		.saturn {
			width: 640px;
			height: 470px;
		}

		.uranus {
			width: 100px;
			height: 100px;
		}

		.neptune {
			width: 80px;
			height: 80px;
		}

		.pluto {
			width: 25px;
			height: 25px;
		}
	}

	@media only screen and (max-width: 962px) {
		.moon {
			width: 25px;
			height: 25px;
		}

		.mercury {
			width: 33px;
			height: 33px;
		}

		.venus {
			width: 50px;
			height: 50px;
		}

		.mars {
			width: 40px;
			height: 40px;
		}

		.jupiter {
			width: 110px;
			height: 110px;
		}

		.saturn {
			width: 100px;
			height: 100px;
		}

		.uranus {
			width: 100px;
			height: 100px;
		}

		.neptune {
			width: 80px;
			height: 80px;
		}

		.pluto {
			width: 25px;
			height: 25px;
		}
	}

	@media only screen and (max-width: 480px) {
		.moon {
			width: 25px;
			height: 25px;
		}

		.mercury {
			width: 33px;
			height: 33px;
		}

		.venus {
			width: 50px;
			height: 50px;
		}

		.mars {
			width: 40px;
			height: 40px;
		}

		.jupiter {
			width: 110px;
			height: 110px;
		}

		.saturn {
			width: 80px;
			height: 80px;
		}

		.uranus {
			width: 100px;
			height: 100px;
		}

		.neptune {
			width: 80px;
			height: 80px;
		}

		.pluto {
			width: 25px;
			height: 25px;
		}
	}
</style>
