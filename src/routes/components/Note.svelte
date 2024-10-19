<script>
	/** @type {{children?: import('svelte').Snippet}} */
	let { children } = $props();
</script>

<div>
	<strong>Note:</strong> {@render children?.()}
</div>

<style>
	div {
		background: #cceeee;
		color: #668383;
		padding: 0.4em 0.7em;
		border-radius:0.5em;
	}
</style>