<script>
	export let header;
	export let value;
</script>

<div class="footer-item">
	<div class="header">{header}</div>
	<div class="value">{value}</div>
</div>

<style>
	.footer-item {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
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
