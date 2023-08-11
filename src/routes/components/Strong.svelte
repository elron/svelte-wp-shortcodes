<script>
	export let color;
	export let classes;
</script>

<strong style="color: {color};" class={classes}>
	<slot />
</strong>

<style>
	:global(body) .text-xl {
		font-size:1.5em;
	}
</style>