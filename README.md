# Svelte WP Shortcodes

Effortlessly blend Svelte components into content with WordPress-inspired shortcodes. Simplify dynamic embedding with a familiar touch.

[Demo](https://svelte.dev/repl/9be6fef779144a93926289a1c0ec6781?version=4.1.2)

## 🚀 Features

- 📌 **Dynamic Embeds**: Seamlessly integrate Svelte components into static content.  
- 🔄 **Props Transfer**: Directly pass shortcode attributes as Svelte props.  
- ✒️ **Versatile Syntax**: Supports both self-closing ([component]) and pair tags ([component]...[/component]), allowing you to write shortcodes with or without quotes around attribute values ([youtube id="123"] or [youtube id=123]).  
- 🎟️ **Slot Support**: Easily pass content between opening and closing shortcodes, which gets rendered using Svelte's `<slot>` mechanism. It also supports `export let slot` if you need the slot content as a variable.
- 🧱 **HTML Compatibility**: Seamless integration with HTML content! the library won't interfere with your HTML structure.
- 🌐 **SSR Compatibility**: Ready for SvelteKit's server-side rendering.  
- 🛠️ **Custom Components**: Fully adaptable with your custom Svelte components for personalized designs.  
- 📦 **Unlimited Shortcodes**: Embed any number of Svelte components or shortcodes without restrictions. 
- 📜 **Multi-Line Support:** Captures and processes shortcodes with content that spans multiple lines, ensuring a flexible and forgiving user experience.



## 📦 Installation

```bash
# pnpm
pnpm install @elron/svelte-wp-shortcode@latest

# npm
npm install @elron/svelte-wp-shortcode@latest

# Yarn
yarn install @elron/svelte-wp-shortcode@latest
```

## 🛠️ Quick Start

1. **Import the Shortcodes component and your custom Svelte components**:
```ts
import WpShortcodes from '@elron/svelte-wp-shortcode';

// Import Your Own Custom Svelte Components
import TryButton from './TryButton.svelte';
import Note from './Note.svelte';
import Youtube from './Youtube.svelte';
import Strong from './Strong.svelte';
```

2. **Use the shortcodes in your content**:
```svelte
<WpShortcodes 
    markup={`
        Simple embed: [try-button]
        Text within: [note]Here's some inner text![/note]
        With properties: [youtube id=EVP1NQAnpYk]
        All combined: [strong color="red" class="text-xl"]Awesome, right?[/strong]
        With HTML: <i>Still works!<i>
    `}
    components={{
        'try-button': TryButton, 
        'note': Note,
        'youtube': Youtube,
        'strong': Strong
    }} 
/>
```

Voilà! The `<TryButton>`, `<Note>`, `<Youtube>`, and `<Strong>` Svelte components are rendered based on their respective shortcode types. Obviously, you can replace them with your own components.


## Notes

- For the shortcode attributes, you must use double quotes `[example message="hey"]` or no quotes at all `[example message=hey]`. Single quotes won't work.
- The library does not support for nested shortcodes. It's optimized for simpler use cases, but deeper nesting or intricate scenarios might require special attention.
- The attribute `slot` is reserved so you can use `export let slot` if needed (`<slot />` is supported as well). Example: If this is the shortcode `[shortcode slot="Initial Content"]Overridden Content[/shortcode]` then `export let slot` the `slot` value will become `Overriden Content`.


## ❤️ Contributing
Your input is valued! Share your feedback, report bugs, or make pull requests on our GitHub repository.


## 📜 License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.

