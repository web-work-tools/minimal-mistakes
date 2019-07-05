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
published: false
last_modified_at: 2019-07-05T11:22:33-23:00
author: infominer
---

This is another guide, while I'm doing it, may as well record all of the steps, so others can re-produce.

I made a considerable effort to copy all of the links that are on the Decentralized-id.com website into our new [discord server](https://discord.gg/eYm2XvZ). The idea is the replicate what I already did for a much broader subject, in [SourceCrypto](https://sourcecrypto.pub/blog/research-index/.

So now, lets see about publishing this archive.


## Discord Chat Exporter

* [Tyrrrz/DiscordChatExporter/wiki](https://github.com/Tyrrrz/DiscordChatExporter/wiki)
  * [Windows Install](https://github.com/Tyrrrz/DiscordChatExporter/releases/latest)
  * [Mac Usage Instructions](https://github.com/Tyrrrz/DiscordChatExporter/wiki/macOS-usage-instructions)
  * [Linux Usage Instructions](https://github.com/Tyrrrz/DiscordChatExporter/wiki/Linux-usage-instructions)
    * [Debian](https://github.com/Tyrrrz/DiscordChatExporter/wiki/Linux-usage-instructions#debian-9)
    * [Ubuntu](https://github.com/Tyrrrz/DiscordChatExporter/wiki/Linux-usage-instructions#ubuntu-18)
  * [Docker Usage Instructions](https://github.com/Tyrrrz/DiscordChatExporter/wiki/Docker-usage-instructions)

## Token and Channel IDs

Your token id is private, and gives full control of your account. Be careful, don't lose it or hand it out.

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
$ ./DiscordChatExporter.Cli.exe exportguild -t "Mzkljafsdo8#*(U300953u90P(UPJIORUE893V9FhHPbqBSVdI" -g 590057677523255296
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

![](https://imgur.com/2sF9YVw.png)

Above is an example html file produced by this process. Although you could also export to csv if you'd prefer to put your own stylings on it.

Over on SourceCrypto, I was publishing them all as Collections. This is a jekyll feature that makes it simple to throw a group of documents together and have them navigable via gridview. Ultimately it's another way to organize content, but I found that more than 9 collections breaks the theme...

So if we want to organize in more than 9 categories, and I think that we do... we'll have to use more than just the collections feature for our archive.

## Editing with VSCode

I'm not sure if I can get it to export by category.. so for now I just organize them by hand. I'll put that on my to-do list. I often procrastinate on learning new automation techniques, so I can better learn the things I'm studying now, and I enjoy the repetitive work.

So I made a folder called `didiscolog`, within it, created a folder for each category on the discord server, and placed that entire archive into our project directory. 

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

![](https://imgur.com/Ku8UCHV.png)

I won't elaborate too much on that right now except to say that with a few lines of code I was able to give each file proper frontmatter.


```yaml    
---
title: "DIDisco - eula"
---
```


I'm not sure what the best way to do this is, I just copy paste sections of those pages I want to remove, such as their custom css. Like many things I do, this system is clunky and works for me, for now.

Probably if I use DiscordChatExporter to make csv rather than html, it will be easier to display.

However, since every file created by the exporter is identical, even my clunky way of doing things isn't too much of a hassel.


There's just one more problem is that these filenames are ridiculous. I have a bulk file renamer that will take care of them

![](https://imgur.com/tRHiy0R.png)

Regex to the rescue, once again!

## Jekyll Collections 