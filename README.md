# Svelte WP Shortcodes

Effortlessly blend Svelte components into content with WordPress-inspired shortcodes. Simplify dynamic embedding with a familiar touch.

## 🚀 Features

- 📌 **Dynamic Embeds**: Seamlessly integrate Svelte components into static content.  
- 🔄 **Props Transfer**: Directly pass shortcode attributes as Svelte props.  
- ✒️ **Versatile Syntax**: Supports both self-closing ([component]) and pair tags ([component]...[/component]), allowing you to write shortcodes with or without quotes around attribute values ([youtube id="123"] or [youtube id=123]).  
- 🎟️ **Slot Support**: Easily pass content between opening and closing shortcodes, which gets rendered using Svelte's `<slot>` mechanism.  
- 🧱 **HTML Compatibility**: Seamless integration with HTML content! the library won't interfere with your HTML structure.
- 🌐 **SSR Compatibility**: Ready for SvelteKit's server-side rendering.  
🛠️ **Custom Components**: Fully adaptable with your custom Svelte components for personalized designs.  
- 📦 **Limitless Integration**: Embed any number of Svelte components or shortcodes without restrictions. 
- 👥 **Basic Nested Support**: The library offers initial support for nested shortcodes. It's optimized for simpler use cases, but deeper nesting or intricate scenarios might require special attention.


## 📦 Installation

```bash
pnpm install svelte-wp-shortcodes
// Or use npm
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
        All combined: [strong color='red' class='text-xl']Awesome, right?[/all-in-one]
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



## ❤️ Contributing
Your input is valued! Share your feedback, report bugs, or make pull requests on our GitHub repository.


## 📜 License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.

