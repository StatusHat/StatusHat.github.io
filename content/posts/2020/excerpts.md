---
title: Not much except excerpts
date: 2020-12-10 # 21:02 +0100
categories: blog
tags:
  - jekyll
  - blog
---

I figured out how to include excerpts of blog posts on the front page/post list. Hopefully, it doesn't look quite as spartan and sad now.

<!--more-->

As it turns out, nothing more is required than adding a line in the frontmatter of the post:

    excerpt_separator: "<!--more-->"

You can use whatever separator you want, of course. Putting this in every post might just be the kind of thing I forget all the time, so thankfully it's possible to stick it in _\_config.yml_ and have it work for all posts.

# In other news

The ["About" page](/about) is now "personal" instead of prewritten stuff about jekyll themes.
