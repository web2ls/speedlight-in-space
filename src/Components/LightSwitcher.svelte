<script>
	import { fade } from 'svelte/transition';

	export let active;
	export let onClick;
</script>

<div
	class="light-switcher {active ? 'active' : ''}"
	on:click={onClick}
	on:keypress={onClick}
>
	{#if !active}
		<svg
			in:fade={{ delay: 100 }}
			class="light-off"
			enable-background="new 0 0 32 32"
			height="32px"
			id="svg2"
			version="1.1"
			viewBox="0 0 32 32"
			width="32px"
			xml:space="preserve"
			><g id="background"
				><rect fill="none" height="32" width="32" y="0" /></g
			><g id="light_x5F_off"
				><path
					d="M32,2l-2-2l-4.174,4.174C24.246,1.934,21.453-0.028,17.001,0c-5.355-0.035-8.315,2.806-9.645,5.552   C5.993,8.293,6.005,10.916,5.999,11c0.036,4.424,2.714,7.911,3.82,9.182L2,28l2,2l7.46-7.46c0.132,0.326,0.244,0.65,0.319,0.951   c0.111,0.443,0.167,0.834,0.194,1.108C12,24.872,11.996,24.999,12,24.999V30h2l2,2h2l2-2h2v-5.039c0-0.04,0.002-0.142,0.025-0.361   c0.074-0.83,0.443-2.677,1.681-3.894c0.051-0.084,4.249-4.165,4.292-9.707c-0.003-0.071,0.001-1.951-0.814-4.183L32,2z    M11.144,18.659C10.078,17.388,7.982,14.339,8,11c0-0.002-0.002-0.531,0.142-1.397c0.214-1.303,0.768-3.249,2.067-4.799   C11.517,3.26,13.499,2.016,17.001,2c4.071,0.031,6.142,1.695,7.378,3.622L11.235,18.765C11.204,18.729,11.178,18.7,11.144,18.659z    M25.854,9.603C26.001,10.469,25.993,11,25.999,11c0.004,2.228-0.908,4.321-1.853,5.851c-0.47,0.764-0.941,1.383-1.293,1.808   c-0.351,0.424-0.562,0.632-0.562,0.634c-1.558,1.593-2.047,3.548-2.206,4.708h-6.171c-0.104-0.758-0.356-1.854-0.947-2.967   L25.589,8.411C25.705,8.84,25.797,9.249,25.854,9.603z"
				/></g
			></svg
		>
	{/if}

	{#if active}
		<svg
			in:fade={{ delay: 100 }}
			class="light-on"
			enable-background="new 0 0 32 32"
			height="32px"
			id="svg2"
			version="1.1"
			viewBox="0 0 32 32"
			width="32px"
			xml:space="preserve"
			><g id="background"
				><rect fill="none" height="32" width="32" y="0" /></g
			><g id="light"
				><path
					d="M26.644,5.553c-1.33-2.746-4.29-5.587-9.643-5.552c-5.355-0.035-8.315,2.806-9.645,5.552   C5.993,8.293,6.005,10.916,5.999,11c0.045,5.542,4.243,9.623,4.292,9.707c0.824,0.817,1.266,1.896,1.488,2.785   c0.111,0.443,0.167,0.834,0.194,1.108C12,24.872,11.996,24.999,12,24.999V30h2l2,2h2l2-2h2v-5.039c0-0.04,0.002-0.142,0.025-0.361   c0.074-0.83,0.443-2.677,1.681-3.894c0.051-0.084,4.249-4.165,4.292-9.707C27.994,10.916,28.006,8.293,26.644,5.553z    M24.146,16.851c-0.47,0.764-0.941,1.383-1.293,1.808c-0.351,0.424-0.562,0.632-0.562,0.634c-1.558,1.593-2.047,3.548-2.206,4.708   h-6.171c-0.16-1.16-0.649-3.115-2.208-4.708c0,0-0.21-0.21-0.562-0.634C10.078,17.388,7.982,14.339,8,11   c0-0.002-0.002-0.531,0.142-1.397c0.214-1.303,0.768-3.249,2.067-4.799C11.517,3.26,13.499,2.016,17.001,2   c4.644,0.035,6.685,2.195,7.854,4.447c0.566,1.13,0.858,2.29,1,3.156C26.001,10.469,25.993,11,25.999,11   C26.003,13.228,25.091,15.321,24.146,16.851z"
				/></g
			></svg
		>
	{/if}
</div>

<style>
	.light-switcher {
		position: relative;
		width: 40px;
		height: 40px;
		display: flex;
		justify-content: center;
		align-items: center;
		border: 2px solid var(--gray);
		border-radius: 10px;
		cursor: pointer;
		z-index: 1;
	}

	.light-switcher svg {
		fill: var(--gray);
	}

	.light-switcher:hover {
		border: 2px solid var(--base-color);
	}

	.light-switcher:hover svg {
		fill: var(--base-color);
	}

	.light-switcher.active svg {
		fill: var(--orange);
	}

	@media only screen and (max-width: 1200px) and (orientation: landscape) {
		.light-switcher {
			width: 35px;
			height: 35px;
		}

		.light-switcher svg {
			width: 20px;
			height: 20px;
		}
	}
</style>
