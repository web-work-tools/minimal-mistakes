---
title: "Minimal-Mistakes-Jekyll - Setup and Configuration"
description: "Contributing to the websites of DIDecentral via GitHub, Jekyll and Minimal Mistakes."
excerpt: >
  This is to help anyone to understand how we're using Minimal Mistakes to publish this and other web-sites. For contributors, or your own use, outside of this organization.
#header:
#  image: assets/img/minimal-mistakes-quickstart-header.png
#  teaser: assets/img/minimal-mistakes-teaser.png
#  og_image: assets/img/minimal-mistakes-teaser.png
#  caption: "Minimal Mistakes Setup and [Quick-Start](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)."
tags: 
  - Configuration
  - Minimal-Mistakes
  - GitHub-Pages
  - Web-Pub
  - How-To
toc_sticky: false
classes: wide
#authors: 
#  - "<a href='https://infominer.id'>Infominer</a>"
#  - "<a href='https://www.caballerojuan.com'>JuanSC</a>"
permalink: website-configuration/
categories: [Contributors-Guide]
published: true
last_modified_at: 2019-07-05T11:22:33-23:00
---

I'm creating this resource while I do the initial setup so that DIDecentral, the Organization, has a guide to how its websites work. This will compliment [decentralized-id.com](https://decentralized-id.com), and support its co-creation.

This guide should make it easier for contributors to understand how this site works, or even for you to use this guide and create your own web-site!

Granted, you don't *need* to know any of this to participate with and contribute to this resource. I'm sharing this here, for anyone who wants to see how this site works.

Soon, there will other guides that simplify onboarding, so that anyone can contribute to this resource, via their preferred social platform.

## Why Minimal Mistakes?

Generally speaking, I like to use and learn know a variety of [static site generators](https://web-work.tools/static-site-generators/) and theier themes. 

However, I've used Minimal Mistakes to publish large websites and small web-sites. It really works. It works well. Even before you know how to use all of it's features, its a really reliable framework.

It supports an incredible variety of functions that simply work. So for building public-domain educational resources, it makes sense for me to stick with what's tried and true.  I've tried to find other themes that offer a comprable feature set, and it's not easy.

Much respect to [Michael Rose](https://mademistakes.com/)!! 

I've used a few of his themes; they are well put together, often ported to other SSGs besides Jekyll, and really a class of their own when it comes to Jekyll themes.

## Getting Started

* [Minimal-Mistakes Quick-Start Guide](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)
* [GitHub Pages Starter Pack](https://web-work.tools/github-pages-starter-pack)

You shouldn't need the above for our imediate purposes, but will likely find them useful at some point.

* [mmistakes/minimal-mistakes](https://github.com/mmistakes/minimal-mistakes/)
* [didecentral/decentralized-id.com](https://github.com/didecentral/decentralized-id.com)
* [didecentral/didecentral.github.io](https://github.com/didecenral/didecentral.github.io)


### Pre-requisites

You must have installed [Git](https://web-work.tools/command-line-git-ssh/),` and the [Ruby Bundler](https://bundler.io/).

I'll also recommend using [VSCode](https://web-work.tools/content-creation/), because it's fully integrated with `git`, so that you don't have to worrying about learning git commands.

Also, I usually create a new repository on github, first. Then I clone it locally, again, avoiding the terminal. Meaning we can learn git in more depth, at our leisure.

Feel free to [ask in chat](https://discord.gg/eYm2XvZ) if you have any questions.

### [Site Structure](https://mmistakes.github.io/minimal-mistakes/docs/structure/)

Before we get started, here is a high-level view of the site-structure.

* [minimal-mistakes](https://github.com/mmistakes/minimal-mistakes/)

```
minimal-mistakes
├── _data                      # data files for customizing the theme
|  ├── navigation.yml          # main navigation links
|  └── ui-text.yml             # text used throughout the theme's UI
├── _includes
|  ├── analytics-providers     # snippets for analytics (Google and custom)
|  ├── comments-providers      # snippets for comments
|  ├── footer                  # custom snippets to add to site footer
|  ├── head                    # custom snippets to add to site head
|  ├── feature_row             # feature row helper
|  ├── gallery                 # image gallery helper
|  ├── group-by-array          # group by array helper for archives
|  ├── nav_list                # navigation list helper
|  ├── toc                     # table of contents helper
|  └── ...
├── _layouts
|  ├── archive-taxonomy.html   # tag/category archive for Jekyll Archives plugin
|  ├── archive.html            # archive base
|  ├── categories.html         # archive listing posts grouped by category
|  ├── category.html           # archive listing posts grouped by specific category
|  ├── collection.html         # archive listing documents in a specific collection
|  ├── compress.html           # compresses HTML in pure Liquid
|  ├── default.html            # base for all other layouts
|  ├── home.html               # home page
|  ├── posts.html              # archive listing posts grouped by year
|  ├── search.html             # search page
|  ├── single.html             # single document (post/page/etc)
|  ├── tag.html                # archive listing posts grouped by specific tag
|  ├── tags.html               # archive listing posts grouped by tags
|  └── splash.html             # splash page
├── _sass                      # SCSS partials
├── assets
|  ├── css
|  |  └── main.scss            # main stylesheet, loads SCSS partials from _sass
|  ├── images                  # image assets for posts/pages/collections/etc.
|  ├── js
|  |  ├── plugins              # jQuery plugins
|  |  ├── vendor               # vendor scripts
|  |  ├── _main.js             # plugin settings and other scripts to load after jQuery
|  |  └── main.min.js          # optimized and concatenated script file loaded before </body>
├── _config.yml                # site configuration
├── Gemfile                    # gem file dependencies
├── index.html                 # paginated home page showing recent posts
└── package.json               # NPM build scripts
```


### CSS - Stylesheets

At the moment, I'm quite CSS agnostic. One thing at a time.. However, if you wanted to add a little style to the page, the community might appreciate that. 

* [mmistakes.github.io/minimal-mistakes/docs/stylesheets/](https://mmistakes.github.io/minimal-mistakes/docs/stylesheets/)

The theme’s assets/css/main.css file is built from several SCSS partials located in _sass/ and is structured as follows:

```
minimal-mistakes
├── _sass
|  └── minimal-mistakes
|     ├── vendor               # vendor SCSS partials
|     |   ├── breakpoint       # media query mixins
|     |   ├── magnific-popup   # Magnific Popup lightbox
|     |   └── susy             # Susy grid system
|     ├── _animations.scss     # animations
|     ├── _archive.scss        # archives (list, grid, feature views)
|     ├── _base.scss           # base HTML elements
|     ├── _buttons.scss        # buttons
|     ├── _footer.scss         # footer
|     ├── _masthead.scss       # masthead
|     ├── _mixins.scss         # mixins (em function, clearfix)
|     ├── _navigation.scss     # nav links (breadcrumb, priority+, toc, pagination, etc.)
|     ├── _notices.scss        # notices
|     ├── _page.scss           # pages
|     ├── _print.scss          # print styles
|     ├── _reset.scss          # reset
|     ├── _sidebar.scss        # sidebar
|     ├── _syntax.scss         # syntax highlighting
|     ├── _tables.scss         # tables
|     ├── _utilities.scss      # utility classes (text/image alignment)
|     └── _variables.scss      # theme defaults (fonts, colors, etc.)
├── assets
|  ├── css
|  |  └── main.scss            # main stylesheet, loads SCSS partials in _sass


```

>To make basic tweaks to theme’s style Sass variables can be overridden by adding to `<your_project>/assets/css/main.scss`. For instance, to change the link color used throughout the theme add:

```yaml
$link-color: red;
```
### [_variables.scss](https://github.com/infominer33/infominer33.github.io/blob/master/_sass/minimal-mistakes/_variables.scss)


There are a number of other variables, you may find by following the link. These are the variables I have changed, so far. Before messing with CSS please check the variables, to be sure you aren't doing too much work!

### Changing the Font-Size

* [Upgrade-friendly way of adjusting font sizes globally](https://github.com/mmistakes/minimal-mistakes/issues/1219)

>So what you can do is add any overriding/new CSS after the @import minimal-mistakes;, in your case:

```

@import "minimal-mistakes";

html {
  font-size: 16px; // change to whatever

  @include breakpoint($medium) {
    font-size: 18px; // change to whatever
  }

  @include breakpoint($large) {
    font-size: 20px; // change to whatever
  }

  @include breakpoint($x-large) {
    font-size: 22px; // change to whatever
  }
}
```

Because this theme is entirely responsive, if you want to change the font-size, you should do it like so.

## Minimal Mistakes Initial Setup

I clone minimal-mistakes into the same directory as whatever website I'm working on, so they are right next to eachother.


```
git clone https://github.com/mmistakes/minimal-mistakes.git
```

![](https://imgur.com/m8HG3Dg.png)


Then I copy over these files and directories to the folder that is linked to the github repository where I want to be able to publish it from.


According to the quickstart guide, when forking these can be safely deleted:

```
    .editorconfig
    .gitattributes
    .github
    .git
    /docs
    /test
    CHANGELOG.md
    minimal-mistakes-jekyll.gemspec
    README.md
    screenshot-layouts.png
    screenshot.png
```

I've moved /docs and /test to /example-site, and added .git, since we're cloning the project, but not forking it, we won't be keeping them linked and can also remove the .git file, and then copied everything that's left over to my project directory, that has its own history and .git files.


![](https://imgur.com/FAXK5SK.png)

I might delete some of the layouts and includes, later. test push I'm pretty sure all I need is a `gem-file` and `_config.yml`. The Gem Install means that GitHub will use a Ruby Gem Package that contains everything needed to run the website. You only need the files that you want to customize or configure somehow. For me, I usually need to change the head, and footer, as well as the social share, but I also change the home layout.. well you see it's easier to just have them all to begin with, and later remove a few that I don't need.

Since I don't know hardly anything about CSS, some contributors might want to work on that, and I will learn eventually, so I want those.

### Gemfile

The gem-file must be properly set up to build and test your changes locally. Not necessary for minor changes, but if you get very deep into working on a web-site, you'll not want to depend on live testing every change ;)

I'm following instructions from [Minimal-Mistakes Quick-Start Guide](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/), but also I've figured some of this out as I go.

Change the Gemfile so it looks like so:

```
source 'https://rubygems.org'
gem "minimal-mistakes-jekyll"

gem "jekyll-paginate"
gem "jekyll-sitemap"
gem "jekyll-gist"
gem "jekyll-feed"
gem "jemoji"
gem "jekyll-include-cache"
```

Every plugin listed in your _config.yml should be also listed in your gem-file, if you want it to work locally, and if your features depend on some of these plugins, then its best to put them in the gemfile as well.

Then, once saved, run the bundle command in the root directory of your project.

`bundle install`
then
`bundle update`
then
`bundle exec jekyll serve`

if all went well you should be looking at a screen like this:

![](https://imgur.com/rnfQchG.png)

Honestly I had to change a few things during the creation of this guide, and am not 100% it would guide you safely through a fresh install from scratch. I'm like 95% sure, but I'll try it out soon and make sure.

In the mean-time, this is plenty to get you started learning about how things work, around here.


### _config.yml

I will keep this page updated with whatever is the most recent configuration, with notes of explanation, when necessary.


```yaml
minimal_mistakes_skin    : "dirt" # "air", "aqua", "contrast", "dark", "dirt", "neon", "mint", "plum", "sunrise"

# Site Settings
locale                   : "en-US"
title                    : "DIDecentral"
title_separator          : "-"
name                     : "DIDecentral"
description              : "Community operations and social syndication archive for decentralized-id.com."
url                      : "https://didecentral.com"
baseurl                  : # the subpath of your site, e.g. "/blog"
repository               : didecentral/didecentral.github.io
github: [metadata] #enables access to your github metadata
teaser                   : # path of fallback teaser image, e.g. "/assets/images/500x300.png"
logo                     : https://decentralized-id.com/images/DID.png
masthead_title           : Community Site and Social Archive
# breadcrumbs            : false # true, false (default)
words_per_minute         : 200
```
I'm not set up for comments, yet. It's something I'll figure out, but lately I haven't had the time, and wasn't sucessful previously.

```yaml
# Social Sharing
twitter:
  username               : didecentral
facebook:
  username               :
  app_id                 :
  publisher              :
og_image                 : # Open Graph/Twitter default site image
# For specifying social profiles
# - https://developers.google.com/structured-data/customize/social-profiles
social:
  type                   : # Person or Organization (defaults to Person)
  name                   : # If the user or organization name differs from the site's name
  links: # An array of links to social media profiles

# Analytics
analytics:
  provider               : google
  google:
    tracking_id          : UA-132558656-3
    anonymize_ip         : true


# Site Author
author:
  name             : "DIDecentral"
  avatar           : /assets/images/did-square.png
  bio              : "Open Source, Public Domain, Educational Initiative"
  location         : "Curating the Web"
  links:
    - label: "Email"
      icon: "fas fa-fw fa-envelope-square"
      url: mailto:identitydecentralized@gmail.com
    - label: "Website"
      icon: "fas fa-fw fa-link"
      url: "https://decentralized-id.com"
    - label: "Twitter"
      icon: "fab fa-fw fa-twitter-square"
      url: "https://twitter.com/didecentral"
    - label: "GitHub"
      icon: "fab fa-fw fa-github"
      url: "https://github.com/didecentral"

# Site Footer
footer:
  links:
    - label: "Email"
      icon: "fas fa-fw fa-envelope-square"
      url: mailto:identitydecentralized@gmail.com
    - label: "Website"
      icon: "fas fa-fw fa-link"
      url: "https://decentralized-id.com"
    - label: "Twitter"
      icon: "fab fa-fw fa-twitter-square"
      url: "https://twitter.com/didecentral"
    - label: "GitHub"
      icon: "fab fa-fw fa-github"
      url: "https://github.com/didecentral"


```


## To be continued....