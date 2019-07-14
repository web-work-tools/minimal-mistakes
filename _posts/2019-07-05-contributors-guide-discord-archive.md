---
title: "Publishing Discord Server Archives via Minimal Mistakes"
description: "Publishing Discord server archives with Minimal Mistakes Jekyll via Github Pages."
excerpt: >
  This is to help anyone to understand how we're using Discord to organize information and track contributions, and publishing that content using Minimal Mistakes on this and other websites.
header:
  image: /assets/images/didecentral-discord-archive.png
  teaser: /assets/images/discord-archive-thumb.png
  og_image: /assets/images/discord-archive-thumb.png
tags: 
  - Discord
  - Archives
  - Minimal-Mistakes
  - GitHub Pages
  - Jekyll
  - How-To
toc_sticky: true
#authors: 
#  - "<a href='https://infominer.id'>Infominer</a>"
#  - "<a href='https://www.caballerojuan.com'>JuanSC</a>"
permalink: discord-archive-howto/
categories: ["Contributors Guide", "DIDecentral"]
published: true
last_modified_at: 2019-07-06T11:22:33-23:00
author: infominer
---

This is another guide, while I'm doing it, may as well record all of the steps, so others can re-produce and or improve upon these methods.

I made a considerable effort to copy all of the links that are on the Decentralized-id.com website into our new [discord server](https://discord.gg/eYm2XvZ). The idea is the replicate what I already did for a much broader subject, in [SourceCrypto](https://sourcecrypto.pub/blog/research-index/.

The site as it is now is a demonstration of a basic initial setup. Consider this site to be your personal playground!

Want to learn some web-publishing skills? Awesome! There's not much you can break here that couldn't be fixed trivially. You don't need to get this technical, but if you are interested in contributing on github, this guide will show you where everything is set up.

## Discord Chat Exporter

This is what makes all of this a real joy. It would not be so simple for me to manually create these archives.

* [Tyrrrz/DiscordChatExporter](https://github.com/Tyrrrz/DiscordChatExporter)
* [Tyrrrz/DiscordChatExporter/wiki](https://github.com/Tyrrrz/DiscordChatExporter/wiki)
  * [Windows Install](https://github.com/Tyrrrz/DiscordChatExporter/releases/latest)
  * [Mac Usage Instructions](https://github.com/Tyrrrz/DiscordChatExporter/wiki/macOS-usage-instructions)
  * [Linux Usage Instructions](https://github.com/Tyrrrz/DiscordChatExporter/wiki/Linux-usage-instructions)
    * [Debian](https://github.com/Tyrrrz/DiscordChatExporter/wiki/Linux-usage-instructions#debian-9)
    * [Ubuntu](https://github.com/Tyrrrz/DiscordChatExporter/wiki/Linux-usage-instructions#ubuntu-18)
  * [Docker Usage Instructions](https://github.com/Tyrrrz/DiscordChatExporter/wiki/Docker-usage-instructions)

### Token and Channel IDs

Your token id is private, and gives full control of your account. Be careful, don't hand it out, or publish it.

[How to get Token and Channel IDs](https://github.com/Tyrrrz/DiscordChatExporter/wiki/Obtaining-Token-and-Channel-IDs)

>How to get User Token
>
> * Press Ctrl+Shift+I (⌘⌥I on Mac) on Discord to show developer tools
> * Navigate to the Application tab
> * Press Ctrl+R (⌘R) to trigger reload
> * Select "Local Storage" > "https://discordapp.com" on the left
> * Find "token" and copy the value

![](/assets/images/discord-token.gif)


>How to get Guild ID or Guild Channel ID

> * Open Discord App Settings
> * Go to Appearance section
> * Enable Developer Mode
> * Right click on the desired guild or channel and click Copy ID

How to get DM Channel ID

> * Open the desired DM channel
> * Press Ctrl+Shift+I (⌘⌥I on Mac) on Discord to show developer tools
> * Navigate to the Console tab
> * Type window.location.href and press Enter
> * Copy the first long sequence of numbers

### Export Scheduling
  * [Windows](https://github.com/Tyrrrz/DiscordChatExporter/wiki/Scheduling-exports-on-Windows)
  * [macOS](https://github.com/Tyrrrz/DiscordChatExporter/wiki/Scheduling-exports-on-macOS)
  * [Linux](https://github.com/Tyrrrz/DiscordChatExporter/wiki/Scheduling-Exports-with-Mono-&-Crontab)


## Exporting DIDecentral
The command I ran looked something like this, and the app is now turning all the channels into complete webpages.:

```
./DiscordChatExporter.Cli.exe exportguild -t "MzMxNDFSdddY0MDI0MzMyMjg4.XR9-pA.7i50GNyuDc5y8IB1oKg" -g 590057677523255296 -f HtmlLight

Exporting channel [101]... 100.0 %
                           Completed ✓
Exporting channel [aml-kyc]... 100.0 %
                               Completed ✓
Exporting channel [apple]... 100.0 %
                             Completed ✓
Exporting channel [aries]... 100.0 %
                             Completed ✓
Exporting channel [asia]... 100.0 %
                            Completed ✓
Exporting channel [ask]... 100.0 %
                           Completed ✓
Exporting channel [assorted]... 100.0 %
                                Completed ✓
Exporting channel [assorted-media]... 100.0 %
                                      Completed ✓
Exporting channel [bigchaindb]... 100.0 %
                                  Completed ✓
Exporting channel [bitcoin]... 100.0 %
                               Completed ✓
Exporting channel [bitcoin-gen]... 100.0 %
                                   Completed ✓
Exporting channel [blockcerts]... 100.0 %
....
```

![](https://imgur.com/wunMbrQ.png)

Above is an example html file produced by this process. Although you could also export to csv if you'd prefer to put your own stylings on it.

I've been using the collections feature of Minimal-Mistakes-Jekyll to publish these records. It's a handy way of organizing information, as we'll see.

I found that more than 9 collections breaks the theme, However, I'm realizing that I have categories also which can be used to further distinguish content within each collection.

## Editing with VSCode

Currently it's only possible to export by category on the windows-app... so for now I just organize them by hand. Sorting all the channels by category is actually probably the most work out of any of it.

I made a folder called `didisco`, within it, created a folder for each category on the discord server, and placed that entire archive into our project directory. 

![](https://imgur.com/p1VFUCS.png)

Now these are complete html files, and we need to remove the head, and just hang on to the content.

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>DIDecentral - eula</title>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width" />

    <style>
        /* === GENERAL === */
```

Each begins like any other html file.

What we want is the just the body, and will use a bit of regex to add some frontmatter:

{% include figure image_path="https://imgur.com/Ku8UCHV.png" alt="Regex Search and Replace VSCode"%}

You can see I used this multiline search with regex:

```
<!Doct.*
.*
.*
.*
    .*DIDecentral - (.*)</title>
```

and replaced it with:

```
---
title: "DIDisco - $1"
---
```

Whenever you surround a regex query with (parenthesis) the text found within that parenthasis on each page can be called with `$1` and if there are more they simply are called `$2` and so forth.

I won't elaborate too much on that right now, but you'll see that with a few lines of code I was able to give each file proper frontmatter.


```yaml    
---
title: "DIDisco - eula"
---
```


I'm not sure what the best way to do this is, I just copy paste sections of those pages I want to remove into the search box. All the pages produced by DiscordChatExporter are identical, and VSCode makes short work of extracting the body of these files..

There's just one more problem is that these filenames are ridiculous. I have a [bulk file renamer](https://docs.xfce.org/xfce/thunar/bulk-renamer/start) that will take care of them.

![](https://imgur.com/TcMYy4L.png)

Regex to the rescue, once again!

## Jekyll Collections 

Now I've sorted all of those files into their individual folders

```
/_application    # Applications -DIDisco
/_public-sector  # Public Sector -DIDisco
/_multi-media    # Multi-Media -DIDisco
/_private-sector # Private Sector -DIDisco
/_resources      # Resources -DIDisco
/_blockchain     # Blockchain -DIDisco
/_organizations  # Organizations -DIDisco
/_tech           # Tech  -DIDisco
/_data 
/_pages
/_posts
/example-site
/assets
/_includes
/.sass-cache
/_sass
/_layouts
```

### _config.yml - Collections

You can go look in our [_config.yml](https://github.com/didecentral/didecentral.github.io/blob/master/_config.yml) to see where I've placed this down near the bottom, but it doesn't really matter.. as long as its indented properly.

These are named the same as our folders without the underscore. I explicitely define folders when the collection name has a dash, otherwise there are problems.

```yaml
collections:
  application:
    output: true
    permalink: /didisco/:collection/:path/
  blockchain:
    output: true
    permalink: /didisco/:collection/:path/
  multi-media:
    output: true
    permalink: "/didisco/multi-media/:path/"
  organizations:
    output: true
    permalink: /didisco/:collection/:path/
  private-sector:
    output: true
    permalink: "/didisco/private-sector/:path/"
  public-sector:
    output: true
    permalink: "/didisco/public-sector/:path/"
  resources:
    output: true
    permalink: /didisco/:collection/:path/
  tech:
    output: true
    permalink: /didisco/:collection/:path/
```

### _config.yml - Frontmatter Defaults

You could add one for pages, as well, these save you from entering the same front-matter over and over.



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

### DiscordChatExporter Stylings

Since I removed the stylings, those pages aren't pretty to look at. There are a few steps to put the stylings back in, just for those exported html-files.

Thanks to [gist-it.appspot.com](https://gist-it.appspot.com), you can see that I have added the stylings into this custom head include. The only thing I changed is that I commented out the body color (white), so that the stylings are made over our "dirt" theme background.

<script src="https://gist-it.appspot.com/https://github.com/didecentral/didecentral.github.io/raw/master/_includes/head/custom.html"></script>


In the [default layout](https://github.com/didecentral/didecentral.github.io/blob/master/_layouts/default.html) I've modified where it calls this custom include:

```
  <head>
    {% include head.html %}
    {% if page.disco %}
      {% include head/custom.html %}
    {% endif %}
  </head>

```

Back in our frontmatter defaults for the didiscolog, you may remember this line:

```
      disco: true
```

That default setting is what triggers the default layout to include our custom stylings.

## Collection Pages

Besides each file generated for our collection, we require a page to list them all, a page for each individual collection, and eventually, pages that distinguish between the categories in each collection as well.

### [_pages/didisco](https://github.com/didecentral/didecentral.github.io/blob/master/_pages/didisco/)

![](https://imgur.com/SaYlNP3.png)

### [index.html](https://github.com/didecentral/didecentral.github.io/blob/master/_pages/didisco/index.html)

* 

{% include figure image_path="https://imgur.com/sVXK1YW.png" alt="Index of DIDiscord Archive" caption="[didecentral.com/didisco/](https://didecentral.com/didisco/)" %}

This is the code that creates the above page.

```html
{% raw %}
---
layout: archive
title: "DIDecentral Social Archive"
permalink: /didisco/
author_profile: false
header:
  image: # /images/source-crypto-disco.png
  teaser: #/images/SourceCrypto-DiscoLog-teaser.png
  caption: #"[SourceCrypto Discord Chat](https://discord.gg/ahTuPMY)"
sidebar:
  nav: "didnav"
classes: wide
share: true

---


{% capture written_label %}'None'{% endcapture %}

{% for collection in site.collections %}
  {% unless collection.output == false or collection.label == "posts" %}
    {% capture label %}{{ collection.label }}{% endcapture %}
    {% if label != written_label %}
      <h2 id="{{ label | slugify }}" class="archive__subtitle">{{ label }}</h2>
      {% capture written_label %}{{ label }}{% endcapture %}
    {% endif %}
  {% endunless %}
  {% for post in collection.docs %}
    {% unless collection.output == false or collection.label == "posts" %}
      {% include archive-single.html %}
    {% endunless %}
  {% endfor %}
{% endfor %}

<section class="page__share">
  <h2>Share or Edit this Page</h2>
  {% if page.disco %}  
    <p><a href="https://github.com/sourcecrypto/sourcecrypto.github.io/edit/master/discolog/{{ page.path }}" class="edit">Edit this page <i class="fa fa-pencil"></i></a></p>
  {% else %}
    <p><a href="https://github.com/sourcecrypto/sourcecrypto.github.io/edit/master/{{ page.path }}" class="edit">Edit this page <i class="fa fa-pencil"></i></a></p>
  {% endif %}
  {% if site.data.ui-text[site.locale].share_on_label %}
    <h4 class="page__share-title">{{ site.data.ui-text[site.locale].share_on_label | default: "Share on" }}</h4>
  {% endif %}

  <a href="https://twitter.com/intent/tweet?{% if site.twitter.username %}via={{ site.twitter.username | url_encode }}&{% endif %}text={{ page.title | url_encode }}%20{{ page.url | absolute_url | url_encode }}" class="btn btn--twitter" onclick="window.open(this.href, 'window', 'left=20,top=20,width=500,height=500,toolbar=1,resizable=0'); return false;" title="{{ site.data.ui-text[site.locale].share_on_label | default: 'Share on' }} Twitter"><i class="fab fa-fw fa-twitter" aria-hidden="true"></i><span> Twitter</span></a>

  <a href="https://www.facebook.com/sharer/sharer.php?u={{ page.url | absolute_url | url_encode }}" class="btn btn--facebook" onclick="window.open(this.href, 'window', 'left=20,top=20,width=500,height=500,toolbar=1,resizable=0'); return false;" title="{{ site.data.ui-text[site.locale].share_on_label | default: 'Share on' }} Facebook"><i class="fab fa-fw fa-facebook" aria-hidden="true"></i><span> Facebook</span></a>

  <a href="https://www.linkedin.com/shareArticle?mini=true&url={{ page.url | absolute_url | url_encode }}" class="btn btn--linkedin" onclick="window.open(this.href, 'window', 'left=20,top=20,width=500,height=500,toolbar=1,resizable=0'); return false;" title="{{ site.data.ui-text[site.locale].share_on_label | default: 'Share on' }} LinkedIn"><i class="fab fa-fw fa-linkedin" aria-hidden="true"></i><span> LinkedIn</span></a>

  <a href="https://www.reddit.com/submit?url={{ page.url | relative_url }}&title={{ page.title }}" class="btn btn--reddit" title="{{ site.data.ui-text[site.locale].share_on_label }} Reddit"><i class="fab fa-fw fa-reddit" aria-hidden="true"></i><span> Reddit</span></a>
</section>
{% endraw %}
```

### [application.md](https://github.com/didecentral/didecentral.github.io/blob/master/_pages/didisco/application.md)

![](https://imgur.com/7dACheO.png)

This page is created by the following front matter, and the configuration settings we set up earlier.

```yaml
---
title: "DIDisco - Application"
layout: collection
permalink: "/didisco/application/"
collection: application
entries_layout: grid
classes: wide
sidebar:
  nav: didnav 
share: true
---
```

For now there are "placeholder" teaser and og_images. Soon we can make custom feature\header images for each page to make the site a bit more inviting.

### Collections Frontmatter - Categories

We only have up to 9 collections, but within those collections we can add directories, categories, and tags for further individiation:

[_tech/specs/dpki.html](https://github.com/didecentral/didecentral.github.io/blob/master/_tech/specs/dpki.html)

```
---
title: "DIDisco - Tech/Specs - dpki"
categories: ["specs", "web-tech"]
---

```

As it stands I made a quick attempt. But I'm hoping we can come up with a limited number of categories that will serve the posts, pages, and collections of this, and perhaps other, websites.



## That's all for now

I think that's all. You should be pretty well set up to duplicate or contribute to this archival process.

I still have to set up navigation for each channel, and cover how that's done, over in the minimal mistakes setup.