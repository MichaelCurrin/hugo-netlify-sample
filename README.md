# Hugo Sample with CMS
> Skeleton Hugo static site based on the Netlify CMS quickstart sample

This is a skeleton/sample project for building a static site with Hugo. It contains both the repo's content and a CMS to make changes to content through a user-friendly frontend.

## Preview

In order to use the local CMS editor, you need to have a user account for the app setup on Netlify Identify. You can then edit the content on Netlify or locally hosted app using the `/admin` path.

When using the _local_ admin view, the content you are editing is in the local repo. But when changes are _published_, a commit is made on the remote repo, without any local commit.

`/admin/#/collections/post`


## Background

This is a small business template built with [Victor Hugo](https://github.com/netlify/victor-hugo) and [Netlify CMS](https://github.com/netlify/netlify-cms), designed and developed by [Darin Dimitroff](http://www.darindimitroff.com/), [spacefarm.digital](https://www.spacefarm.digital).

I got a copy of the repo in my Github account when using the Deploy to Netlify button. I've since edited the repo to have sample content which is more generic. I plan use this is a starting point for new static sites and as simplified working reference for maintaining actual sites.

## Run on Netlify

### Auto setup

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/michaelcurrin/hugo-netlify-sample&stack=cms)

That button points to a Netlify deploy URL with the URL for this repository added as a parameter. The button previously pointed to https://github.com/netlify-templates/one-click-hugo-cms and that is how the base for this project was created.

This will setup everything needed for running the CMS:

- A new repository in your GitHub account with the code
- Full Continuous Deployment to Netlify's global CDN network
- Control users and access with Netlify Identity
- Manage content with Netlify CMS


### Manual setup

Alternatively, manually create an app on the Netlify site and choose a Hugo repo such as this one (or your own fork of it).

The repo's [Netlify config file](/netlify.toml) should provide appropriate details for the build & deploy section of your app.

### Usage

Check in the Netlify logs that your site deployed successfully then find the public URL.

Once the initial build finishes, you can invite yourself as a user. Go to the Identity tab in your new site, click "Invite" and send yourself an invite. Then accept is from your e-mail inbox.

Visit `/admin` on your site to login to the CMS editor. This use Netlify's Identity CMS, to give users the ability to set passwords, login and edit content. Manage your users through your site's settings on Netlify.

Now you're all set and you can start editing content.


## Local development

Follow this section to install and run this Hugo CMS template site. For further tips, see the _Hugo_ section this [static site resources](https://github.com/MichaelCurrin/static-sites-generator-resources) repo.

This project uses a configured `package.json` to run Hugo. You can install and run the Hugo server with either `npm` or `yarn`, as covered below. `yarn` is not as widely used but arguably a better option and so is preferred for this project. To avoid conflicts and a warning message, a `yarn.lock` file is versioned but not `packackage-lock.json`.


### Installation


#### Install OS-level dependencies

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

```bash
$ nvm use 11.0.0
```

#### Clone this repository

```bash
$ git clone https://github.com/michaelcurrin/hugo-netlify-sample
```

#### Install project dependencies


##### Hugo

The project comes with Hugo binaries in the [bin](/bin/) directory. These need to be run in the context of a config file.

```bash
$ cd hugo-netlify-sample
$ cd site
$ ../bin/hugo.darwin version
Hugo Static Site Generator v0.46 darwin/amd64 BuildDate: 2018-08-01T09:00:55Z
```

These binaries came with the base repo and the project was already configured to use it. If the binaries are missing, you will get an error.

Alternatively, install Hugo. However, these docs do not support running a user installed version of hugo.

##### Node packages

```bash
$ npm install
```

OR

```bash
$ yarn install
```

### Usage

Start the development server locally use `npm` or `yarn`. One of these will run the steps needed to process and serve assets for the public and admin views. This includes running `gulp`. Do not attempt to run the Hugo command directly as it will build to a different directory and you will miss some functionality.

```bash
$ npm start
```

OR

```bash
$ yarn start
```

View the site at http://localhost:1313 (npm) or http://localhost:3000 (yarn) .

Login to the admin view at `/admin`. Note that although you followed the path for the local server, the site you view and any changes you make are actually on the remote repo. i.e. If you add a post, you create a commit in the remote Github repo which triggers a Netlify rebuild - no file changes or commits are made in the local repo.


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
