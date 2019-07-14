---
title: Contributors Quickstart (A Gentle Introduction to GitHub)
permalink: contributors-quickstart/
categories: ["Contributors Guide", "DIDecentral"]
tags: ["Quickstart","Tools", "GitHub Pages", "Minimal Mistakes"]
publsihed: false
---

So far, we've covered quite a lot of ground in our contributors guides!

* [Welcome DIDecentral](/welcome/) - A high level overview of the projects we're working on.
* [Contributors Intro](/contributors-intro/) - The easiest ways to participate with DIDecentral.
* [Website Configuration](/website-configuration/) - 'Everything' about how this site is configured.
* [Discord Archive HowTo](/discord-archive-howto/) - How to export discord history and integrate with Minimal Mistakes Jekyll.

What is needed is a quickstart guide, so that you don't need to worry about reading all of that just revise content or add a few links to our web-sites.

All that's required to follow this guide is a web-browser and a GitHub account. If you don't already have one, go ahead and [sign up](https://github.com/join) so you can follow along. 
{: .notice--primary}

## Edit This Page

Feel free to submit test pull-requests while following along or exploring on GitHub.

![](https://imgur.com/txuSpMs.png)

Besides using social media, such as [twitter](https://didecentral.com/contributors-intro/#twitter--mention-and-hash-tags) or [discord](https://didecentral.com/contributors-intro/#contributing-via-discord), the simplest way to contribute to these web-sites is by clicking "Edit this page", which should be found at the bottom of every page run by DIDecentral.

If everything is properly set up on our side of things, you will find yourself transported from our website to that pages source file on GitHub.

<img src="https://didecentral.com/assets/images/edit-this-page.png" alt="Pencil Edit Button on GitHub Source File">

If you click the little pencil icon (red circle in above image), you will find a basic text editor and the pages source. If you don't have commit access to the repository, a patch copy of that file will be created in your github account where you can edit, and propose changes.

![](https://imgur.com/2UEOj9V.png)


## Front Matter

This is where configuration on the page level happens.   

```yaml
---
---
title: "Welcome to DIDecentral Community Site and Social Archive"
description: "DIDecentral is a collaborative curation initiative aiming to create quality educational content related to Decentralized Identity: Principles, Specs, Code and Initiatives."

# the excerpt is what supplies preview text on the post-index.

excerpt: > 
  A high-level overview of our organization, its projects, and their general state of development.
header:
  image: /assets/images/didecentral-community-header.png
  teaser: /assets/images/didecentral-community-teaser.png
  caption: ""
tags: 
  - "Decentralized Identity"
  - "Web of Trust"
  - "Self Sovereign Identity"
  - Archive
  - How-To
categories: ["DIDecentral", "Welcome"]
author: Infominer

#If you are making some revisions to existing content you can use the following example that will add a contributors section at the bottom of the page near tags and categories (be sure to uncomment and edit those lines to fit the situation of whatever page you are on).
authors: 
  - #"<a href='https://infominer.id'>Infominer</a>"
  - #"<a href='https://www.caballerojuan.com'>JuanSC</a>"

#If you want to change a permalink, you must add the current permalink to the `redirect_from` list,  or create one if it does not already exist.
permalink: welcome/
redirect_from:
  - welcome-didecentral/
  - welcome
  - welcome-didecentral
toc_sticky: true
published: true
last_modified_at: 2019-07-10T11:22:33-23:00
#Be sure to change the modified date. I create my own custom made-up time, with the actual date. You can simply ignore the time, and update the date, or use whatever you'd like for the time. Later, the most recently modified content will be featured.
---
```

In yaml documents, and the yaml front-matter of posts, the #hashtag is used for comments. Hopefully with the commented front-matter above, it's reasonably clear how the configuration of a page works. There are other page settings, but this covers all the essentials.


## Saving your changes

Once you've completed any edits, whether you've added a link or corrected a spelling error, leave a simple comment explaining what type of change you're proposing.

![](https://imgur.com/2s6Kspq.png)

Once you've submitted a change, GitHub compares the original with your proposed changes and asks if you'd like to create a pull-request.

![](https://imgur.com/rWSn2nr.png)

Assuming you're happy with the changes (in green at the bottom) go ahead and create a pull-request.

![](https://imgur.com/1ak7bhi.png)

Leave a comment explaining your changes. There is plenty of room to be as descriptive as you want in the pull-request comments, compared to the commit comment which is typically short.

## Checking on your Pull-Request

You should get an e-mail notifying you of any updates related to your pull-request. However, you can always see updates related to your open issues and pull-requests by clicking the GitHub logo at the top of any page on GitHub.

![](https://imgur.com/qAEcp7w.png)


That feed also includes notifications for any individuals you follow or repositories you watch.

![](https://imgur.com/EQQdzri.png)

Since the account I used to create this guide doesn't follow anyone or have any activity, here's an example of an active feed:

![](https://imgur.com/PBhPqtH.png)

If you don't have time to get into GitHub, don't feel obliged to read any further. Above should be plenty to begin making simple contributions, as you browse, without getting too technical.
{: .notice--primary}

## Fork didecentral.github.io

One advantage of forking the repository is that you can make as many changes as you like, and take as long as you want in your local repository. Then submit a pull-request when you're satisfied.

![](/assets/images/fork-repository.png)

Now you'll have a copy of the repository in your account.

![](https://imgur.com/8lNavU8.png)

## Write a Blog Post

Since you have full permissions to this repository, you can upload files or create them right in your browser!

This site is for the community. Anyone is welcome to sumbit a post. This should be a low-stakes environment where anyone could learn to use GitHub and GitHub Pages for the first time. 

Even if you just want to write about what brings you to DIDecentral, share what project you are working on. If you aren't currently working on anything identity related, that's fine, share what you'd like, use your imagination.

The idea is to be as welcoming as possible, and encourage people to try it out. Editing text files on GitHub is a gateway to digital transformation. 

You don't have to be very technical to get started. If you start with the simple things, after a while, you'll find that you're getting to know the lay of the land. It's possible to build from there to learn any number of technical skills, as @infominer33 has been discovering.

![](https://imgur.com/lIn4hRm.png)


Click "Create new file" where the hand pointer is in the illustration, above the file listing, below the "watch" icon.

Name your post starting with the date, and then the title, with `-` dashes instead of spaces.

`YEAR-MONTH-DAY-title.md`


```
---
title:  "Hi I'm info-bot!"
---

**Hello world**, this is my first Jekyll blog post.

I hope you like it!

I'm an account that @infominer33 uses for experimenting with various features.

This post was written during the creation of {{% raw %}{{ site.baseurl }}{% post_url 2019-07-13-contributors-quickstart.md %}.{% endraw %}

```



### More Info on Posts

The theme we are using, Minimal Mistakes, is built on Jekyll, you can learn more about how Jekyll uses posts, here:

* [jekyllrb.com/docs/posts](https://jekyllrb.com/docs/posts/)

