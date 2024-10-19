<script lang="ts">
	import { Highlight } from 'svelte-highlight';
	import { xml } from 'svelte-highlight/languages';

	import 'svelte-highlight/styles/vs2015.css';

	interface Props {
		slot: string;
	}

	let { slot }: Props = $props();
</script>

<Highlight language={xml} code={slot.replaceAll('&lt;', '<')} />
