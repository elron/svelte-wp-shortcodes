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

1. **Import the Shortcodes component and your custom Svelte components**:
```ts
import WpShortcodes from '@elron/svelte-wp-shortcode';

// Import Your Own Custom Svelte Components
import SelfClosed from './SelfClosed.svelte';
import WithSlot from './WithSlot.svelte';
import WithProps from './WithProps.svelte';
import AllInOne from './AllInOne.svelte';
```

2. **Use the shortcodes in your content**:
```svelte
<WpShortcodes 
    markup="
        Simple embed: [self-closed].
        Text within: [with-slot]Here's some inner text![/with-slot].
        With properties: [with-props prop1='Hello' prop2='World'].
        All combined: [all-in-one prop1='Svelte' prop2='Shortcodes']Awesome, right?[/all-in-one].
    "
    components={{
        'self-closed': SelfClosed, 
        'with-slot': WithSlot,
        'with-props': WithProps,
        'all-in-one': AllInOne
    }} 
/>
```

Voilà! The `<SelfClosed>`, `<WithSlot>`, `<WithProps>`, and `<AllInOne>` Svelte components are rendered based on their respective shortcode types. Obviously, you can replace them with your own components.



## ❤️ Contributing
Your input is valued! Share your feedback, report bugs, or make pull requests on our GitHub repository.


## 📜 License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.

