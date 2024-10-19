<script lang="ts">
	interface Props {
		id: string;
		title?: string;
	}

	let { id, title = '' }: Props = $props();
</script>

<!-- <small>Youtube Video ID: {id}</small> -->
<div>
	<iframe
		src="https://www.youtube.com/embed/{id}"
		{title}
		frameborder="0"
		allow="autoplay; picture-in-picture; clipboard-write"
		allowfullscreen
	></iframe>
</div>
