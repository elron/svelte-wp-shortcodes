# Svelte WP Shortcodes

Elevate your Svelte apps with the power of WordPress-like shortcodes! This library allows you to dynamically embed Svelte components within static or dynamic content using the familiar shortcode syntax.

## 🚀 Features

📌 **Dynamic Embeds**: Seamlessly integrate Svelte components into static content.  
🔄 **Props Transfer**: Directly pass shortcode attributes as Svelte props.  
🌐 **SSR Compatibility**: Ready for SvelteKit's server-side rendering.  
👥 **Basic Nested Support**: The library offers initial support for nested shortcodes. It's optimized for simpler use cases, but deeper nesting or intricate scenarios might require special attention.  

## 📦 Installation

```bash
npm install svelte-wp-shortcodes
```

## 🛠️ Quick Start

1. **Import the Shortcodes component**:
```ts
import WpShortcodes from '@elron/svelte-wp-shortcode';
```

2. **Specify your Svelte components**:
```ts
import MyComponent from './MyComponent.svelte';
```

3. **Use the shortcodes in your content**:
```svelte
<WpShortcodes markup="Here's a special feature: [my-component prop='value']" components={{'my-component': MyComponent}} />
```

... and voilà! Your Svelte component MyComponent gets rendered wherever the shortcode is placed.

## 💡 Notes
- Supports both self-closing ([component]) and pair tags ([component]...[/component]).
- Developed with love and tested for compatibility with SvelteKit's server-side rendering.


## ❤️ Contributing
Your input is valued! Share your feedback, report bugs, or make pull requests on our GitHub repository.



