# Shopify Gulp Skeleton

A super-simple starter theme for a 100%-custom Shopify site.

The overall Skeleton is built using Shopify's [Theme Kit](https://shopify.github.io/themekit), I just added the following:

- Gulp style processing
- SCSS mixins for easier Shopify assets
- A couple starter sections since I always forget how to add them properly

## Setting up theme development

### 1. Install Theme Kit

See if it's already installed, skip if so:

```shell
$ theme --help
```

More detailed instructions can be found [here](http://shopify.github.io/themekit/).

```shell
$ brew tap shopify/shopify
$ brew install themekit
```

### 2. Clone this skeleton

```shell
$ cd path/to/projects
$ git clone git@github.com:sambrannon/shopify-gulp-skeleton.git PROJECT_NAME
```

### 3. Clone theme on store

Shopify is weird, we need an ID to do a theme sync, but that ID can only be grabbed from an existing theme. You can create it via CLI, but it will make this skeleton harder to use.

1. Go to https://STORE_NAME.myshopify.com/admin/themes
2. Select current theme > Actions > Duplicate
3. Rename duplicated theme to whatever you'd like

### 4. Get ID of new theme

```shell
$ theme get --list -p=PASSWORD_WITHOUT_QUOTES -s=STORE_NAME.myshopify.com
```

### 5. Fill out config

From the project root directory, add a `config.yml` file and fill it out according to the `config.yml.example` file.

Your API key can be found via https://site-name.myshopify.com/admin/apps/private.

Apply theme ID to config.yml, ie:

```yml
development:
  password: PASSWORD_FROM_PRIVATE_APP
  theme_id: THEME_ID
  store: SHOP_NAME.myshopify.com
```

### 6. Update `settings_schema.json`

Update the values in the default schema file.

Note: `"name": "theme_info",` needs to stay as-is!

### 7. Sync Initial Theme

```shell
$ theme deploy
```

This will kick off an initial deploy and copy all your local files to Shopify, deleting what was there before.

## Working on theme

### Running Theme Watch

Once you are set up, start a theme watch to keep the live site in sync.

```shell
$ theme watch
```

### Running Gulp to process styles

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
