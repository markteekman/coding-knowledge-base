Components can't have attributes like HTML tags can. So if you wan't to use something like the `class` attribute on your component when you use it, you'll have to provide it as a prop:

```jsx
---
const { class: classNames } = Astro.props
---

<div class={classNames}>
	<slot />
</div>
```

[More information on the official Astro docs](https://docs.astro.build/en/guides/styling/#passing-a-class-to-a-child-component)