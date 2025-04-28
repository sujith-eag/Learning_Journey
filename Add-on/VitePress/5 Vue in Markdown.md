
In VitePress, each Markdown file is compiled into HTML and then processed as a [Vue Single-File Component](https://vuejs.org/guide/scaling-up/sfc.html). This means you can use any Vue features inside the Markdown, including dynamic templating, using Vue components, or arbitrary in-page Vue component logic by adding a `<script>` tag.

All Vue usage needs to be SSR-compatible. See [SSR Compatibility](https://vitepress.dev/guide/ssr-compat) for details and common workarounds.


___

## `<script>` and `<style>`

Root-level `<script>` and `<style>` tags in Markdown files work just like they do in Vue SFCs, including `<script setup>`, `<style module>`, etc. The main difference here is that there is no `<template>` tag: all other root-level content is Markdown. Also note that all tags should be placed **after** the frontmatter:

```
---
hello: world
---

<script setup>
import { ref } from 'vue'

const count = ref(0)
</script>

## Markdown Content

The count is: {{ count }}

<button :class="$style.button" @click="count++">Increment</button>

<style module>
.button {
  color: red;
  font-weight: bold;
}
</style>
```

.
.
.
.
.
.
.
.
.
