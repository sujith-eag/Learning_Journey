The config file can be split by environment, root, configuration, root, language etc

`config/_default` can have `hugo.toml`, `menues.en.toml`, `params.toml`
`config/production` can have `params.toml`

The root configuration keys are 
`build`, `caches`, `cascade`, `deployment`, `frontmatter`, `imaging`, `languages`, `markup`, `mediatypes`, `menues`, `module`, `outputformats`, `outputs`, `params`, `permalinks`, `privacy`, `related`, `security`, `segments`, `server`, `services`, `sitemap`, `taxonomies`

In a `hugo.toml` file, the key has to be specified before deatails
```toml
[params]
	foo ='bar'
```
If a config file is made with config key, then Omit the configuration key inside the file.
If file is `params.toml`, no need to mention `[params]`
```toml
foo="bar"
```

Various sub directories can be created inside `config` as `_default`, `production`, `staging`

By default hugo sets environment to `development` when running hugo server.
if `config/development` is missing it uses `config/_default`.

The `production/hugo.toml` can contain some fields that should be merged while building the site.

while running `hugo` the environment is set to `production`


[configuration](https://gohugo.io/getting-started/configuration/)
check all configuration settings
