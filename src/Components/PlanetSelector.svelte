<script>
	let isVisible = false;

	function toggleList() {
		isVisible = !isVisible;
	}
</script>

<div class="planet-selector">
	<div class="selected" on:click={toggleList} on:keypress={toggleList}>
		Moon
	</div>
	{#if isVisible}
		<ul class="planet-list">
			<li class="planet-list__item">Mars</li>
			<li class="planet-list__item">Saturn</li>
			<li class="planet-list__item">Jupiter</li>
		</ul>
	{/if}
</div>

<style>
	.planet-selector {
		position: relative;
		width: 100px;
		margin-right: 20px;
		cursor: pointer;
		z-index: 10;
		border: 2px solid var(--gray);
		border-radius: 10px;
	}

	.selected {
		position: relative;
		padding: 10px;
		text-align: center;
	}

	.planet-list {
		position: relative;
		padding: 0;
		margin: 0;
		list-style-type: none;
		color: var(--base-color);
		text-align: center;
	}

	.planet-list__item {
		cursor: pointer;
	}

	.planet-list__item:hover {
		color: var(--orange);
	}
</style>
