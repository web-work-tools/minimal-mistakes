---
title: "Publishing Discord Server Archives via Minimal Mistakes"
description: "Publishing Discord server archives with Minimal Mistakes Jekyll via Github Pages."
excerpt: >
  This is to help anyone to understand how we're using Discord to organize information and track contributions, and publishing that content using Minimal Mistakes on this and other websites.
#header:
#  image: assets/img/minimal-mistakes-quickstart-header.png
#  teaser: assets/img/minimal-mistakes-teaser.png
#  og_image: assets/img/minimal-mistakes-teaser.png
#  caption: "Minimal Mistakes Setup and [Quick-Start](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)."
tags: 
  - Discord
  - Archives
  - Minimal-Mistakes
  - GitHub-Pages
  - Jekyll
  - Web-Pub
  - How-To
toc_sticky: false
classes: wide
#authors: 
#  - "<a href='https://infominer.id'>Infominer</a>"
#  - "<a href='https://www.caballerojuan.com'>JuanSC</a>"
permalink: discord-archive-howto/
categories: [Contributors-Guide]
published: true
last_modified_at: 2019-07-06T11:22:33-23:00
author: infominer
---

This is another guide, while I'm doing it, may as well record all of the steps, so others can re-produce and or improve upon these methods.

I made a considerable effort to copy all of the links that are on the Decentralized-id.com website into our new [discord server](https://discord.gg/eYm2XvZ). The idea is the replicate what I already did for a much broader subject, in [SourceCrypto](https://sourcecrypto.pub/blog/research-index/.

So now, lets see about publishing this archive. 


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

## Token and Channel IDs

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

## Export Scheduling
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

```
collections:
  application:
    output: true
    permalink: /discolog/:collection/:path/
  blockchain:
    output: true
    permalink: /discolog/:collection/:path/
  multi-media:
    output: true
    permalink: "/discolog/multi-media/:path/"
  organizations:
    output: true
    permalink: /discolog/:collection/:path/
  private-sector:
    output: true
    permalink: "/discolog/private-sector/:path/"
  public-sector:
    output: true
    permalink: "/discolog/public-sector/:path/"
  resources:
    output: true
    permalink: /discolog/:collection/:path/
  tech:
    output: true
    permalink: /discolog/:collection/:path/
```

### _config.yml - Frontmatter Defaults

You could add one for pages, as well, these save you from entering the same front-matter over and over.

```
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
```

### DiscordChatExporter Stylings

