---
title: Dockerify the thing
date: 2021-11-11 # 20:00 +01:00
category: blog
tags:
  - docker
---

Last post ended on a frustrated note. Arch Linux is on Ruby 3 which Jekyll doesn't support yet. No rbenv-wrangling would get things work locally. It sucked.

<!--more-->

Things I contemplated

- quitting
- setting up a multi-version environment where I could hotplug any kind of ruby or gem version - wait! That's what I was trying all along.
- quitting
- Throwing out my command line shell for another with different principles regarding path and environment variables and such in the hope that would maybe help
- quitting
- migrating this whole blog to Hugo or Gatsby or Pelican or any one of [these][1]
- also migrating to another service, like Netlify - or even Wordpress
- quitting

Then I stumbled upon some blog post on running Jekyll in a container. Which I think makes complete sense in my situation. So I began reading up on how Docker works and trying to create and get a Jekyll image up and running. Followed by contemplating

- quitting. again.

Then I found [this blog post][2] that seemed to neatly sum up what I wanted and what I needed to do. I installed docker and docker-compose (easy peasy, and it seems even docker-compose might be unnecessary) and created an exact copy of that guy's `docker-compose.yml` in my blog repo folder. Then I hit `docker-compose up` and waited while all the gems in my Gemfile were installed and after no more than a minute the server was up.

Voila! The blog was there. If I made an edit to a post, it was in my browser in an instant.

Next step was to tear out all versions of rubies and gems and hugo and gatsby and jekyll and bundler and everything from my real OS. Kick them out. Really kick them. It felt real good.

Future steps: Go over the dependencies in my Gemfile. What's needed what's not what's up to date what's not. And wrap my head around using docker and compose more properly. Learn the basics. Make sure I can handle it if something small changes, or if I need to swap image or something. All future steps! Oh, and make something of the blank space to the left, maybe!

[1]: https://jamstack.org/generators/
[2]: https://enriquecatala.com/2020/05/28/Creating-my-new-blog-with-Jekyll.html
