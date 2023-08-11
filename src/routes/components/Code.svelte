<script lang="ts">
	import { Highlight } from 'svelte-highlight';
	import { xml } from 'svelte-highlight/languages';

	import 'svelte-highlight/styles/vs2015.css';

	export let slot: string;
</script>

<Highlight language={xml} code={slot.replaceAll('&lt;', '<')} />
