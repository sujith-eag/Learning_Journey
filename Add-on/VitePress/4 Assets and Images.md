
## Referencing Static Assets

All Markdown files are compiled into Vue components and processed by [Vite](https://vitejs.dev/guide/assets.html). You can, **and should**, reference any assets using relative URLs:

```
![An image](./image.png)
```

Linked files are not treated as assets

PDFs or other documents referenced by links within markdown files are not automatically treated as assets. To make linked files accessible, you must manually place them within the [`public`](https://vitepress.dev/guide/asset-handling#the-public-directory) directory of your project.

All referenced assets, including those using absolute paths, will be copied to the output directory with a hashed file name in the production build. Never-referenced assets will not be copied. Image assets smaller than 4kb will be base64 inlined - this can be configured via the [`vite`](https://vitepress.dev/reference/site-config#vite) config option.

All **static** path references, including absolute paths, should be based on your working directory structure.


___

You can place these files in the `public` directory under the [source directory](https://vitepress.dev/guide/routing#source-directory). For example, if your project root is `./docs` and using default source directory location, then your public directory will be `./docs/public`.

Assets placed in `public` will be copied to the root of the output directory as-is.

Note that you should reference files placed in `public` using root absolute path - for example, `public/icon.png` should always be referenced in source code as `/icon.png`.

> [!note]
This kind of didn't work in GitHub


___

