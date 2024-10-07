<script lang="ts">
	// Props expected by this Svelte component
	export let markup: string; // A string containing HTML-like markup with possible custom shortcodes
	export let components: { [key: string]: any } = {}; // An object mapping shortcode names to Svelte components (e.g., { 'Button': ButtonComponent })

	// Variables to store parsed information
	let componentInstances: any[] = []; // Will hold details about the instances of components found in `markup`
	let parsedMarkup: any[] = []; // Will store the final mixed content of plain text and component instances for rendering

	// This reactive block will run whenever `markup` or `components` changes
	$: {
		// Object to store regex patterns for all available shortcodes
		let shortcodePatterns: { [pattern: string]: any } = {};

		// Create regex patterns for each shortcode name in `components`
		for (let componentName in components) {
			// For each component name (e.g., 'Button'), create a regex pattern to match its format in `markup`
			// The regex supports content between opening and closing tags (like [Button]content[/Button]) or self-closing tags (like [Button attr="value"])
			shortcodePatterns[
				`\\[${componentName}(.*?)(?:\\]([\\s\\S]*?)\\[/${componentName}\\]|\\])`
			] = components[componentName];
		}

		// Function to extract attributes from a shortcode string (e.g., `attr="value"`)
		function extractAttributes(attrString: string): { [key: string]: string } {
			// Trim whitespace, split by spaces to isolate attributes, and reduce into an object
			let attrs = attrString
				.trim()
				.split(' ')
				.reduce((acc: { [key: string]: string }, curr) => {
					// Each attribute has a key and an optional value (like `attr="value"`)
					let [key, value] = curr.split('=');
					// Remove quotes around the value, if present, and add to `acc`
					acc[key] = value?.replace(/"/g, ''); 
					return acc;
				}, {}); // Start with an empty object
			return attrs;
		}

		// Reset `componentInstances` to collect new instances whenever `markup` is parsed
		componentInstances = [];

		// Parse `markup` for any shortcodes that match the regex patterns
		for (let pattern in shortcodePatterns) {
			let regex = new RegExp(pattern, 'g'); // Create a regex for each shortcode pattern
			let match;

			// Find all matches for the current shortcode pattern in `markup`
			while ((match = regex.exec(markup)) !== null) {
				// Extract attributes (if any) and inner content from the match
				let attributesString = match[1]; // The attribute string from the opening tag
				let content = match[2] || ''; // Content between opening and closing tags, or empty if self-closing
				let props = extractAttributes(attributesString); // Convert attribute string to an object of attributes

				// Store details of this shortcode instance, including its position in `markup`
				componentInstances.push({
					start: match.index, // Where this match starts in the `markup`
					end: match.index + match[0].length, // Where this match ends in the `markup`
					component: shortcodePatterns[pattern], // The Svelte component associated with the shortcode
					props: props, // Attributes converted to an object
					content: content // Inner content between shortcode tags
				});
			}
		}

		// Build `parsedMarkup`, which mixes strings and component instances for rendering
		parsedMarkup = [];
		let lastIndex = 0; // Tracks the last processed index in `markup`
		
		// Sort `componentInstances` by their positions in `markup` to process in order
		componentInstances
			.sort((a, b) => a.start - b.start)
			.forEach((item) => {
				// Add any plain text that comes before the current component
				parsedMarkup.push(markup.slice(lastIndex, item.start));
				// Add the current component instance (as an object)
				parsedMarkup.push(item);
				// Update `lastIndex` to the end of the current component
				lastIndex = item.end;
			});
		
		// After all components are added, add any remaining plain text after the last component
		parsedMarkup.push(markup.slice(lastIndex));
	}
</script>

<!-- Render `parsedMarkup` using a loop (`each` block) -->
{#each parsedMarkup as item, index (index)}
	{#if typeof item === 'string'}
		<!-- If `item` is a plain string, render it as HTML -->
		{@html item}
	{:else}
		<!-- If `item` is a component instance, dynamically render it with its props -->
		<svelte:component this={item.component} {...item.props} slot={item.content}>
			<!-- The content between the shortcode tags is passed as the default slot content -->
			{item.content}
		</svelte:component>
	{/if}
{/each}
