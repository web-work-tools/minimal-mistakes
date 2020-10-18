---
title: "Using HTML Proofer to Find and Fix Broken Links"
excerpt: "This guide explains how to use an HTML proofer to find broken links, so we can fix them and stop being mad at broken links."
tags: ["ToDo"]
categories: ["Contributors-Guide"]
published: true
permalink: /contributors-guide/html-proofer/
canonical_url: https://web-work.tools/minimal-mistakes/contributors-guide/html-proofer/
---

We all know how much it sucks when links are broken. Especially the internal links we use to navigate within these sites. If you're interested to help out, but wondering if there's an easier way than clicking each link and hunting through the source to fix the reference, this is the guide for you!

I'm assuming you have already gotten a local copy of this site, and are familiar with our [Website Configuration](website-configuration/). Soon there will be a simple and straightforward guide for copying  site and testing our site locally, so you won't have to study that huge guide just to test the waters.

## [gjtorikian/html-proofer](https://github.com/gjtorikian/html-proofer)

>HTMLProofer is a set of tests to validate your HTML output. These tests check if your image references are legitimate, if they have alt tags, if your internal links are working, and so on. It's intended to be an all-in-one checker for your output.
>
>In scope for this project is any well-known and widely-used test for HTML document quality. A major use for this project is continuous integration -- so we must have reliable results. We usually balance correctness over performance. And, if necessary, we should be able to trace this program's detection of HTML errors back to documented best practices or standards, such as W3 specifications.

### Install


```ruby
source 'https://rubygems.org'
gem "minimal-mistakes-jekyll"

gem "jekyll-paginate"
gem "jekyll-sitemap"
gem "jekyll-gist"
gem "jekyll-feed"
gem "jemoji"
gem "jekyll-include-cache"
gem "jekyll-mentions"
gem 'html-proofer'
```

Then you must type `bundle install` from the root of your local copy.

Once installed, you can run Html Proofer as a command-line app. 

There's [a lot of other ways](https://github.com/gjtorikian/html-proofer) to use it, but here's a simle example that gives us some actionable results:

`htmlproofer --disable_external --directory_index_file index.html --empty_alt_ignore ./_site`

