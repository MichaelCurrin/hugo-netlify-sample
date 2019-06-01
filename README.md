# Hugo Sample with CMS
> Hugo template site for Netlify CMS, with Netlify Identity

This is a skeleton/sample project for building a static site with Hugo. It contains both the repo's content and a CMS to make changes to content through a user-friendly frontend.

*I've had issues getting the CMS editor to work locally but it works great when deployed to the Netlify site.*

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

### Installation

#### OS-level dependencies

This project requires `node`. Note that version 12 and up cause issues with the gulp server, so based on a Stack Overflow answer, install and older version of node or use the node version manager.

```bash
$ brew install nodejs
```

```bash
$ brew install nvm
```

```bash
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
$ yarn
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

View the site at http://localhost:3000 .

Login to the admin view at http://localhost:3000/admin .


## Customization tips from the original repo

### Layouts

The template is based on small, content-agnostic partials that can be mixed and matched. The pre-built pages showcase just a few of the possible combinations. Refer to the `site/layouts/partials` folder for all available partials.

Use Hugo’s `dict` functionality to feed content into partials and avoid repeating yourself and creating discrepancies.

### CSS

The template uses a custom fork of *Tachyons* and *PostCSS* with *cssnext* and *cssnano*. To customize the template for your brand, refer to `src/css/imports/_variables.css` where most of the important global variables like colors and spacing are stored.

### SVG

All SVG icons stored in `site/static/img/icons` are automatically optimized with *SVGO* (*gulp-svgmin*) and concatenated into a single SVG sprite stored as a a partial called `svg.html`. Make sure you use consistent icons in terms of viewport and art direction for optimal results. Refer to an SVG via the `<use>` tag like so:

```html
<svg width="16px" height="16px" class="db">
  <use xlink:href="#SVG-ID"></use>
</svg>
```
