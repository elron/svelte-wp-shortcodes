<script>
	import WpShortcodes from '$lib/WpShortcodes.svelte';

	// Import Your Own Custom Svelte Components
	import HiButton from './components/HiButton.svelte';
	import Note from './components/Note.svelte';
	import Youtube from './components/Youtube.svelte';
	import Strong from './components/Strong.svelte';
	import Code from './components/Code.svelte';
</script>

<!-- <WpShortcodes
	components={{
		'hi-button': HiButton,
		note: Note,
		youtube: Youtube,
		strong: Strong,
		code: Code
	}}
	markup={`
        <p>Simple embed: [hi-button]</p>
        <p>Text within: [note]Here's some inner text![/note]</p>
        <p>With properties: [youtube id=EVP1NQAnpYk]</p>
        <p>All combined: [strong color="red" classes="text-xl"]Awesome, right?[/strong]</p>
        <p>With HTML: <i>Still works!<i></p>
		

<pre class="wp-block-code">[code]<script
    src="https://run.confettipage.com/here.js"
    data-confetticode="..."
    data-trigger="custom"
></script>[/code]</pre>

    `}
/> -->
<WpShortcodes
	components={{
		'hi-button': HiButton,
		note: Note,
		youtube: Youtube,
		strong: Strong,
		code: Code
	}}
	markup={`
        <p>Simple embed: [hi-button]</p>

    `}
/>
