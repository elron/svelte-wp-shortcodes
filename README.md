# Svelte WP Shortcodes

Effortlessly blend Svelte components into content with WordPress-inspired shortcodes. Simplify dynamic embedding with a familiar touch.

## 🚀 Features

📌 **Dynamic Embeds**: Seamlessly integrate Svelte components into static content.  
🔄 **Props Transfer**: Directly pass shortcode attributes as Svelte props.  
✒️ **Versatile Syntax**: Supports both self-closing ([component]) and pair tags ([component]...[/component]).  
🎟️ **Slot Support**: Easily pass content between opening and closing shortcodes, which gets rendered using Svelte's `<slot>` mechanism.  
🌐 **SSR Compatibility**: Ready for SvelteKit's server-side rendering.  
🛠️ **Custom Components**: Fully adaptable with your custom Svelte components for personalized designs.  
📦 **Limitless Integration**: Embed any number of Svelte components or shortcodes without restrictions.  
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


## ❤️ Contributing
Your input is valued! Share your feedback, report bugs, or make pull requests on our GitHub repository.



