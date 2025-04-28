.
.
.
.
.
.
.

# Extending the Default Theme

VitePress' default theme is optimized for documentation, and can be customized. Consult the [Default Theme Config Overview](https://vitepress.dev/reference/default-theme-config) for a comprehensive list of options.


However, there are a number of cases where configuration alone won't be enough. For example:

1. You need to tweak the CSS styling;
2. You need to modify the Vue app instance, for example to register global components;
3. You need to inject custom content into the theme via layout slots.

These advanced customizations will require using a custom theme that "extends" the default theme.


___

