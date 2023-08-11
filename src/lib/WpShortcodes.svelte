<script lang="ts">
	export let markup: string;
	export let components: { [key: string]: any } = {};

	let componentInstances: any[] = [];
	let parsedMarkup: any[] = [];

	$: {
		let shortcodePatterns: { [pattern: string]: any } = {};

		// Generate regex patterns based on provided components
		for (let componentName in components) {
			// Doesnt support multi line
			// shortcodePatterns[`\\[${componentName}(.*?)(?:\\](.*?)\\[/${componentName}\\]|\\])`] =
			// Supports multi line
			shortcodePatterns[`\\[${componentName}(.*?)(?:\\]([\\s\\S]*?)\\[/${componentName}\\]|\\])`] =
				components[componentName];
		}

		function extractAttributes(attrString: string): { [key: string]: string } {
			let attrs = attrString
				.trim()
				.split(' ')
				.reduce((acc: { [key: string]: string }, curr) => {
					let [key, value] = curr.split('=');
					acc[key] = value?.replace(/"/g, ''); // remove quotes if present
					return acc;
				}, {});
			return attrs;
		}

		componentInstances = [];

		// Parse the markup for any shortcode and replace with the corresponding component
		for (let pattern in shortcodePatterns) {
			let regex = new RegExp(pattern, 'g');
			let match;

			while ((match = regex.exec(markup)) !== null) {
				let attributesString = match[1];
				let content = match[2] || '';
				let props = extractAttributes(attributesString);

				componentInstances.push({
					start: match.index,
					end: match.index + match[0].length,
					component: shortcodePatterns[pattern],
					props: props,
					content: content
				});
			}
		}

		// Construct the parsedMarkup array for rendering
		parsedMarkup = [];
		let lastIndex = 0;
		componentInstances
			.sort((a, b) => a.start - b.start)
			.forEach((item) => {
				parsedMarkup.push(markup.slice(lastIndex, item.start));
				parsedMarkup.push(item);
				lastIndex = item.end;
			});
		parsedMarkup.push(markup.slice(lastIndex));
	}
</script>

{#each parsedMarkup as item, index (index)}
	{#if typeof item === 'string'}
		{@html item}
	{:else}
		<svelte:component this={item.component} {...item.props} slot={item.content}>
			{item.content}
		</svelte:component>
	{/if}
{/each}
