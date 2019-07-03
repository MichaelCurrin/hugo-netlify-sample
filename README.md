# Hugo Sample with CMS
> Skeleton Hugo static site based on the Netlify CMS quickstart sample

This is a skeleton/sample project for building a static site with Hugo. It contains both the repo's content and a CMS to make changes to content through a user-friendly frontend.

## Preview

In order to use the local CMS editor, you need to have a user account for the app setup on Netlify Identify. You can then edit the content on the Netlify or locally hosted app using the `/admin` path.

When using the local admin view, the content content you are editing is in the local repo. But when changes are published is a commit is made on the remote repo without any local commit


`/admin/#/collections/post`



## Background

This is a small business template built with [Victor Hugo](https://github.com/netlify/victor-hugo) and [Netlify CMS](https://github.com/netlify/netlify-cms), designed and developed by [Darin Dimitroff](http://www.darindimitroff.com/), [spacefarm.digital](https://www.spacefarm.digital).

I got a copy of the repo in my Github account when using the Deploy to Netlify button. I've since edited the repo to have sample content which is more generic. I plan use this is a starting point for new static sites and as simplified working reference for maintaining actual sites.

## Run on Netlify

### Auto setup

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/michaelcurrin/hugo-netlify-sample&stack=cms)

*(The button points to a Netlify deploy URL with a repository sent as a parameter. This was previously https://github.com/netlify-templates/one-click-hugo-cms and that is how this repo was created before I changed it.)*

This will setup everything needed for running the CMS:

* A new repository in your GitHub account with the code
* Full Continuous Deployment to Netlify's global CDN network
* Control users and access with Netlify Identity
* Manage content with Netlify CMS


### Manual setup

Alternatively, manually create an app on the Netlify site and choose a Hugo repo such as this one (or your own fork of it).

The repo's [Netlify config file](netlify.toml) should provide appropriate details for the build & deploy section of your app.

### Usage

Check in the Netlify logs that your site deployed successfully then find the public URL.

Once the initial build finishes, you can invite yourself as a user. Go to the Identity tab in your new site, click "Invite" and send yourself an invite. Then accept is from your e-mail inbox.

Visit `/admin` on your site to login to the CMS editor.

Now you're all set, and you can start editing content.


## Local development

This project uses a configured `package.json` to run Hugo.

You can install and run the Hugo server with either `npm` or `yarn`, as covered below. `yarn` is not as widely used but arguably a better option and so is preferred for this project. To avoid conflicts and a warning message, a `yarn.lock` file is versioned but not `packackage-lock.json`.


### Installation

#### OS-level dependencies

This project requires `node`. Note that version 12 and up cause issues with the gulp server, so based on a Stack Overflow answer, install and older version of node or use the node version manager.

```bash
$ brew install nodejs
```

```bash
$ brew install nvm yarn
```

Choose a version older than 12. Install it once off.

```bash
$ nvm install 11.0.0
```

Activate it whenever you need to work with this repo.

```
$ nvm use 11.0.0
```


#### Clone this repository

```bash
$ git clone https://github.com/michaelcurrin/hugo-netlify-sample
```

#### Install dependencies


```bash
$ npm install
```

OR

```bash
$ yarn install
```

### Usage

Start the development server locally.

```bash
$ npm start
```

OR

```bash
$ yarn start
```

View the site at http://localhost:1313 (npm) or http://localhost:3000 (yarn) .

Login to the admin view at `/admin`.


## Customization tips

### Config

The projects config is [/site/config.toml](/site/config.toml).

### Admin

See the files in [admin](/site/static/admin/) directory. The config file determines what pages can be edited and what fields they have. The index file is the admin login page.

### Layouts

The template is based on small, content-agnostic partials that can be mixed and matched. The pre-built pages showcase just a few of the possible combinations. Refer to the [partials](/site/layouts/partials) folder for all available partials.

Use Hugo’s `dict` functionality to feed content into partials and avoid repeating yourself and creating discrepancies.

### CSS

The template uses a custom fork of *Tachyons* and *PostCSS* with *cssnext* and *cssnano*. To customize the template for your brand, refer to [_variables.css](/src/css/imports/_variables.css) where most of the important global variables like colors and spacing are stored.


### Images

The [img](/site/static/img/) directory is where `.jpeg`, `.png`, `.ico` and `.svg` files are stored.


#### SVG

All SVG icons stored in [icons](/site/static/img/icons) are automatically optimized with *SVGO* (*gulp-svgmin*) and concatenated into a single SVG sprite stored as a a partial called `svg.html`. Make sure you use consistent icons in terms of viewport and art direction for optimal results. Refer to an SVG via the `<use>` tag like so:

```html
<svg width="16px" height="16px" class="db">
    <use xlink:href="#SVG-ID"></use>
</svg>
```
