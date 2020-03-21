# Shopify Gulp Skeleton

A super-simple starter theme for a 100%-custom Shopify site.

The overall Skeleton is built using Shopify's [Theme Kit](https://shopify.github.io/themekit), I just added the following:

- Gulp style processing
- SCSS mixins for easier Shopify assets
- A couple starter sections since I always forget how to add them properly

## Setting up theme development

Install [Theme Kit](http://shopify.github.io/themekit/). More detailed instructions can be found [here](http://shopify.github.io/themekit/).

```shell
$ brew tap shopify/shopify
$ brew install themekit
```

From the project root directory, add a `config.yml` file and fill it out according to the `config.yml.example` file.

Your API key can be found via https://site-name.myshopify.com/admin/apps/private.

TODO: Add docs for deploying a new theme entirely from local without using `theme new...`...

```shell
$ theme configure --password=[your-password] --store=[you-store.myshopify.com] --themeid=[your-theme-id]
```

From there, start a theme watch to keep the live site in sync.

```shell
$ theme watch
```

## Gulp

Gulp is used in tandem with some custom Shopify-friendly scss mixins (/styles/functions/_shopify-helpers.scss)

Build style with Gulp to process SCSS, then replace all function instances with the Liquid tag versions.

This allows writing of "pure" scss and won't throw warnings/errors since they are translated to Liquid variables after compilation.

```shell
$ yarn build
```

Watch for changes via

```shell
$ yarn build-watch
```
