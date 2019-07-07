---
title: "Minimal-Mistakes-Jekyll - Setup and Configuration"
description: "Contributing to the websites of DIDecentral via GitHub, Jekyll and Minimal Mistakes."
excerpt: >
  This is to help anyone to understand how we're using Minimal Mistakes to publish this and other web-sites. For contributors, or your own use, outside of this organization.
header:
  image: /assets/images/minimal-mistakes-quickstart-header.png
  teaser: /assets/images/minimal-mistakes-teaser.png
  og_image: /assets/images/minimal-mistakes-teaser.png
  caption: "Minimal Mistakes Setup and [Quick-Start](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)."
tags: 
  - Configuration
  - Minimal-Mistakes
  - GitHub-Pages
  - Web-Pub
  - How-To
toc_sticky: true
#classes: wide
authors: 
  - "<a href='https://infominer.id'>Infominer</a>"
  - "<a href='https://www.caballerojuan.com'>JuanSC</a>"
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
masthead_title           : For Decentralized Sovereign Identification Online
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

I just went to [fontawesome.com](https://fontawesome.com) and it's pretty simple to try and match above formula without thinking too deeply on the matter.


### _config.yml - Frontmatter Defaults

You can over-ride these defaults on a page-by-page basis.

```yaml
# Defaults
defaults:
  # _posts
  - scope:
      path: "_posts"
      type: posts
    values:
      layout: single
      author_profile: true
      read_time: true
      comments: # true
      share: true
      related: true
      header:
       image: /assets/images/didecentral.png #the image at the top of the page
       og_image: /assets/images/did-og.png #the image preview on twitter, discord, etc.
      sidebar:
        nav: "didnav"
      toc: true
  # _pages
  - scope:
      path: "_pages"
      type: pages
    values:
      layout: single
      author_profile: false
      read_time: true
      comments: # true
      share: true
      related: true
      header:
       image: /assets/images/didecentral.png
       og_image: /assets/images/did-og.png
      sidebar:
        nav: "didnav"
      toc: true
  # _application
  - scope:
      path: "_application"
      type: application
    values:
      layout: single
      share: true
      related: true
      sidebar:
        title: "DID ⧉ Nav"
        nav: "didnav"
      classes: wide
      disco: true
      header:
       image: /assets/images/did-header.png
       og_image: /assets/images/did-og.png
  # _blockchain
  - scope:
      path: "_blockchain"
      type: blockchain
    values:
      layout: single
      share: true
      related: true
      disco: true
      sidebar:
        nav: "didnav"
      classes: wide
      header:
       image: /assets/images/did-header.png
       og_image: /assets/images/did-og.png
    # _multi-media
  - scope:
      path: "_multi-media"
      type: "multi-media"
    values:
      layout: single
      share: true
      disco: true
      related: true
      sidebar:
        nav: "didnav"
      classes: wide
      header:
       image: /assets/images/did-header.png
       og_image: /assets/images/did-og.png
    # _organizations
  - scope:
      path: "_organizations"
      type: organizations
    values:
      layout: single
      share: true
      related: true
      disco: true
      sidebar:
        nav: "didnav"
      classes: wide
      header:
       image: /assets/images/did-header.png
       og_image: /assets/images/did-og.png
    # _private-sector
  - scope:
      path: "_private-sector"
      type: "private-sector"
    values:
      layout: single
      share: true
      related: true
      disco: true
      sidebar:
        nav: "didnav"
      classes: wide
      header:
       image: /assets/images/did-header.png
       og_image: /assets/images/did-og.png
    # _public-sector
  - scope:
      path: "_public-sector"
      type: "public-sector"
    values:
      layout: single
      share: true
      related: true
      sidebar:
        nav: "didnav"
      classes: wide
      disco: true
      header:
       image: /assets/images/did-header.png
       og_image: /assets/images/did-og.png
    # _resources
  - scope:
      path: "_resources"
      type: resources
    values:
      layout: single
      share: true
      related: true
      disco: true
      sidebar:
        nav: "didnav"
      classes: wide
      header:
       image: /assets/images/did-header.png
       og_image: /assets/images/did-og.png
    # _tech
  - scope:
      path: "_tech"
      type: tech
    values:
      layout: single
      share: true
      related: true
      disco: true
      sidebar:
        nav: "didnav"
      classes: wide
      header:
       image: /assets/images/did-header.png
       og_image: /assets/images/did-og.png
```


## Navigation

[_data/navigation.yml](https://github.com/didecentral/didecentral.github.io/blob/master/_data/navigation.yml)

Then if you look up there in the front-matter defaults, you'll see where the navigation is called as a part of the sidebar class.

```yaml
# main links
main:
  - title: "Decentralized-id.com"
    url: https://decentralized-id.com
  - title: "RWoT Papers Index"
    url: https://didecentral.com/rwot-dir
  - title: "Decentralized Web Histories"
    url: https://sourcecrypto.pub/decentralized-web/
  - title: "Static Sites for an IndieWeb"
    url: https://web-work.tools/indieweb
  

# DID Nav

didnav:
  - title: Contributors Guides
    children:
      - title: "Minimal-Mistakes - Configuration"
        url: /website-configuration/
      - title: Discord Archive Walktrhu
        url: /discord-archive-howto/
  - title: DIDisco Archives
    url: /didisco/
    children:
      - title: Resources
        url: /didisco/resources/
      - title: Multi-Media
        url: /didisco/multi-media/
      - title: Blockchain
        url: /didisco/blockchain/
      - title: Organizations
        url: /didisco/organizations/
      - title: Public Sector
        url: /didisco/public-sector/
      - title: Private Sector
        url: /didisco/private-sector/
      - title: Tech
        url: /didisco/tech/
      - title: Application
        url: /didisco/application
```

## Social Share

This is the code that makes social share and donation button on each page. The Bitcoin, Tippin.me, and DOGE addresses are specific for DIDecentral, and currently under @infominer33's control.

[_includes/social-share.html](https://github.com/didecentral/didecentral.github.io/blob/master/_includes/social-share.html)

```html
<section class="page__share">
  <h4>ON GITHUB</h4>
  <p><a href="https://github.com/didecentral/didecentral.github.io/blob/master/{{ page.path }}" class="edit">Edit this page <i class="fa fa-pencil"></i></a></p>
    {% if site.data.ui-text[site.locale].share_on_label %}
  <h4 class="page__share-title">{{ site.data.ui-text[site.locale].share_on_label | default: "Share on" }}</h4>
    {% endif %}
  <a href="https://twitter.com/intent/tweet?{% if site.twitter.username %}via={{ site.twitter.username | url_encode }}&{% endif %}text={{ page.title | url_encode }}%20{{ page.url | absolute_url | url_encode }}" class="btn btn--twitter" onclick="window.open(this.href, 'window', 'left=20,top=20,width=500,height=500,toolbar=1,resizable=0'); return false;" title="{{ site.data.ui-text[site.locale].share_on_label | default: 'Share on' }} Twitter"><i class="fab fa-fw fa-twitter" aria-hidden="true"></i><span> Twitter</span></a>
  <a href="https://www.facebook.com/sharer/sharer.php?u={{ page.url | absolute_url | url_encode }}" class="btn btn--facebook" onclick="window.open(this.href, 'window', 'left=20,top=20,width=500,height=500,toolbar=1,resizable=0'); return false;" title="{{ site.data.ui-text[site.locale].share_on_label | default: 'Share on' }} Facebook"><i class="fab fa-fw fa-facebook" aria-hidden="true"></i><span> Facebook</span></a>
  <a href="https://www.linkedin.com/shareArticle?mini=true&url={{ page.url | absolute_url | url_encode }}" class="btn btn--linkedin" onclick="window.open(this.href, 'window', 'left=20,top=20,width=500,height=500,toolbar=1,resizable=0'); return false;" title="{{ site.data.ui-text[site.locale].share_on_label | default: 'Share on' }} LinkedIn"><i class="fab fa-fw fa-linkedin" aria-hidden="true"></i><span> LinkedIn</span></a>
  <a href="https://www.reddit.com/submit?url={{ page.url | relative_url }}&title={{ page.title }}" class="btn btn--reddit" title="{{ site.data.ui-text[site.locale].share_on_label }} Reddit"><i class="fab fa-fw fa-reddit" aria-hidden="true"></i><span> Reddit</span></a>
  <h4>SUPPORT THE CAUSE</h4>
    <p>Feel free to <a href="mailto:identity.decentralized@gmail.com">contact us</a>!</p>
    <!-- Beginning of tippin.me Button -->
    <p><div id="tippin-button" data-dest="didecentral"></div>
    <script src="https://tippin.me/buttons/tip.js" type="text/javascript"></script></p>
    <!-- End of tippin.me Button -->
  <table class="table table-bordered table-hover table-condensed">
      <thead>
      <tr>
        <th title="Field #1">Bitcoin</th>
        <th title="Field #2">DOGE</th>
      </tr>
      </thead>
      <tbody>
      <tr>
        <td>1D9382Y1hwF9mx8tRu8ZUVxcm2aq6yZDYR</td>
        <td>DQKkzfJjqnXUD8Z7C3e84vKzvghPe9dXSa</td>
      </tr>
      <tr>
        <td><img src="https://didecentral.com/assets/images/bitcoin-address.png" width="150"></td>
        <td><img src="https://didecentral.com/assets/images/doge-address.png" width="150"></td>
      </tr>
    </tbody>
  </table>  
</section>
```

**Reddit Button**

[_sass/minimal-mistakes/_buttons.scss](https://github.com/didecentral/didecentral.github.io/blob/master/_sass/minimal-mistakes/_buttons.scss)

If you copy that part to get the reddit button included with the others, you might find that you are missing the actual button.

just head over to buttons.css :rofl: (idk why that's so funny to me)

```
  /* button colors */
  $buttoncolors:
  (primary, $primary-color),
  (inverse, #fff),
  (light-outline, transparent),
  (success, $success-color),
  (warning, $warning-color),
  (danger, $danger-color),
  (info, $info-color),
  (facebook, $facebook-color),
  (twitter, $twitter-color),
  (linkedin, $linkedin-color),
  (reddit, $reddit-color);
```

Because the Reddit Color is already defined in [_variables.scss](https://github.com/didecentral/didecentral.github.io/blob/master/_sass/minimal-mistakes/_variables.scss), all you need to do is reference it here.

## Author vs Authors

There are two variables that must always be considered.

Author, is for the initial or primary author.
Authors is for all the people who have contributed to that document.

So if you make a new post be sure to set both in your front-matter

```yaml
---
title: "Your Awesome Post"
author: "AwesomeYou"
authors: ["AwesomeYou"]
---
```

Then if I came and touched up your post, I would add myself to the authors:

```yaml
---
title: "Your Awesome Post"
author: "AwesomeYou"
authors: ["AwesomeYou","infominer33"]
---
```

Every post and page should have these, but I'm used to being the only author, so that will require some work, or maybe will leave old articles alone... not sure

### Authors Code

This was really crudely hacked together from the other lists in this section.

[_includes/authors-list.html](https://github.com/infominer33/didecentral.github.io/blob/master/_includes/authors-list.html)

```html

<p class="page__taxonomy">
    <strong><i class="fas fa-fw fa-users" aria-hidden="true"></i> Authors:</strong>
    {% assign authorCount = page.authors | size %}
    {% if authorCount == 0 %}
        No author
    {% elsif authorCount == 1 %}
        {{ page.authors | first }}
    {% else %}
        {% for author in page.authors %}
            {% if forloop.first %}
            <a href="{{ author.url }}" rel="author">{{ author }}</a>
            {% elsif forloop.last %}
                and <a href="{{ author.url }}" rel="author">{{ author }}</a>
            {% else %}
                , <a href="{{ author.url }}" rel="author">{{ author }}</a>
            {% endif %}
        {% endfor %}
    {% endif %}
</p>

```

[/_includes/page__taxonomy.html](https://github.com/infominer33/infominer33.github.io/blob/master/_includes/page__taxonomy.html)

Also, I added this line to the page taxonomy:

```html
{% if page.authors %}
  {% include authors-list.html %}
{% endif %}
```

## To be continued....

There are a number of tweaks that I make to minimal-mistakes sites. All will be explained :D

