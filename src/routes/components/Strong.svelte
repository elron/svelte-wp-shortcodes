<script>
	/** @type {{color: any, classes: any, children?: import('svelte').Snippet}} */
	let { color, classes, children } = $props();
</script>

<strong style="color: {color};" class={classes}>
	{@render children?.()}
</strong>

<style>
	:global(body) .text-xl {
		font-size:1.5em;
	}
</style>