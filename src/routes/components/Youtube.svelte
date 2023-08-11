<script lang="ts">
	export let id: string;
	export let title = '';
</script>

<!-- <small>Youtube Video ID: {id}</small> -->
<div>
	<iframe
		src="https://www.youtube.com/embed/{id}"
		{title}
		frameborder="0"
		allow="autoplay; picture-in-picture; clipboard-write"
		allowfullscreen
	/>
</div>
