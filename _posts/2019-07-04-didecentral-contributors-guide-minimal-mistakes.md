---
title: "DIDecentral Contributors Guide: Minimal-Mistakes-Jekyll Gem-Based Deploy"
---

I'm creating this resource while I do the initial setup for DIDecentral, the Organization, to have its own web-site, to accompany the website, [decentralized-id.com](https://decentralized-id.com), we are co-creating.


This will make it easier for contributors to understand how this site works, or even for you to use this guide and create your own web-site!

## Why Minimal Mistakes?

Generally speaking, I'd like to use and get to know a variety of themes and [static site generators](https://web-work.tools/static-site-generators/). However, I've tried out Minimal Mistakes to publish large websites and small web-sites. It really works. It works well. So for building public-domain educational resources, I love it's features. Much respect to it's creator, [Michael Rose](https://mademistakes.com/). I've used a few of his themes; they are well put together, and often ported to other SSGs besides Jekyll.

## Getting Started

* [Minimal-Mistakes Quick-Start Guide](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)
* [mmistakes/minimal-mistakes](https://github.com/mmistakes/minimal-mistakes/)
* [didecentral/decentralized-id.com](https://github.com/didecentral/decentralized-id.com)
* [didecentral/didecentral.github.io](https://github.com/didecenral/didecentral.github.io)


### Pre-requisites

You must have installed Git and the Ruby Bundler. 

I'll also recommend using [VSCode](https://web-work.tools/content-creation/), because it's fully integrated with `git`, so that you don't have to worrying about learning [git commands](https://web-work.tools/command-line-git-ssh/), right away.

Also, I usually create a new repository on github, first. Then I clone it locally, again, avoiding the terminal. Meaning I can learn git in more depth, at my leisure.

Later there will be more complete guides on all the things, but for now, this should get most of our early contributors started fairly simply, and Infominer (that's me:) is around to help if you get stuck with anything.

### [Site Structure](https://mmistakes.github.io/minimal-mistakes/docs/structure/)

This will give you a high-level view of site-structure, and I've linked to each directory, in its home repository, for easy access.

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

At the moment, I'm quite CSS agnostic. One thing at a time.. However, if you wanted to add a little style to the page, I might not complain. This is how the sytlesheets are named \ organized.

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


Then I copy over these files and directories to the folder that is linked to the github repository where I want to be able to publish it from:

![](https://imgur.com/FAXK5SK.png)

I might delete some of the layouts and includes, later. test push I'm pretty sure all I need is a `gem-file` and `_config.yml`. The Gem Install means that GitHub will use a Ruby Gem Package that contains everything needed to run the website. You only need the files that you want to customize or configure somehow. For me, I usually need to change the head, and footer, as well as the social share, but I also change the home layout.. well you see it's easier to just have them all to begin with, and later remove a few that I don't need.

Since I don't know hardly anything about CSS, some contributors might want to work on that, and I will learn eventually, so I want those.

### Gemfile

The reason we are using the Gem version is because it keeps all the files up to date, if I'm not customizing them. Otherwise, a fork you have to occasionally strip out the old and update.. which isn't necessarily a bad thing, if you're still learning.

I'm following the instructions for a gem based install from [Minimal-Mistakes Quick-Start Guide](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/):

First change the Gemfile so it looks like so:

```
source "https://rubygems.org"

gem "minimal-mistakes-jekyll"
```

Then, once saved, run the bundle command in the root directory of your project.

`bundle`


### _config.yml

Then you must set the theme in your project’s Jekyll _config.yml file, you can see, I've simply uncommented that line. This should be everything we need to get started.


```
theme                  : "minimal-mistakes-jekyll"
# remote_theme           : "mmistakes/minimal-mistakes"
minimal_mistakes_skin    : "dirt" # "air", "aqua", "contrast", "dark", "dirt", "neon", "mint", "plum", "sunrise"

# Site Settings
locale                   : "en-US"
title                    : "DIDecentral Community Site"
title_separator          : "-"
name                     : "DIDecentral"
description              : "A website where the contents of our discord server is published, and information on what we do, and how we do it."
url                      : "https://didecentral.com"
baseurl                  : # the subpath of your site, e.g. "/blog"
repository               : didecentral/didecentral.github.io
github: [metadata] #enables access to your github metadata

```

There are plenty of other configurations, however, most of it is straightforward and I'll mostly explain where it isn't.

First, if you are following very closely, a line must be removed from `_layouts/default.html`, as it references a feature that hasn't been included in the gem-based version, quite yet...


