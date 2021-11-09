---
title: Another day another fumble
date: 2021-11-09 20:52
category: blog
tags: git rtfm jekyll theme
---

Last time I had a short TODO-list at the end of my post. How many have I managed to tick off?

<!--More-->    

 1.   Add pages for posts by year, category and tags

The "Posts by year" bit is embarrassing, because I can't remember how I ended up finding the solution. I think I ended up reading the sources of several blogs that had the features I was aiming for and trying things at random. This bothers me, because I don't really understand how it works.

The file I needed to edit was `_data/navigation.yml`:

    main:
    - title: "Posts"
        url: /posts/
    - title: "Tags"
        url: /tags/
    - title: "About"
        url: /about/

As far as I can see, there is no place to define the behavior of the "Posts" page. Add it to "Navigation" and go. I may be mistaken.

On my todo-list there is also:
 
 1.  Figure out what’s up with the apostrophes around the file name for the “branches and breakage” post in the output of ls _posts command earlier
 
      * This was actually really simple. Some time ago, the age old command `ls` was updated with a feature to improve visibility of the output. The apostrophes are there to tell you that "this is a file and it has spaces in it"
 1. Read slowly and carefully
    * I'm not there yet...

1. Take notes ALL the time, both while reading and of every change and command. Maybe I’ll finally learn something. Or at least finally learn…
    * no not there either

1. Don’t use the IDE (VS Code) for things that can be done on the command line before
    * you know how those things work
    * you know how the IDE works

1. And maybe also get vim (neovim, actually) working as editor in VS Code. Or take a pause from VS Code and just use vim for a while. Those things might also be the subject for upcoming posts.

    * I have installed the Neo Vim plugin, and so far I'm pleased. There are som quirks to get to know, but then I'm not that fluent in vi-like editing yet, anyway...

1. Also: Increase the post width. It's cramped
    
    * Fixed here: index.html

        Also: explain how?
        Yes! Add the following line:
        
        `classes:wide`

Things I also learned:

* Non-commited changes can be commited from any branch. Well at least non-added changes. Need to check again. Just make sure you check branch status before committing
* Jekyll can keep a "draft post" folder. Handy! Create folder _drafts and stuff your drafts and work in progress there. To test, serve your site with the --drafts flag. 

* Version requirements and rolling releases are a bitch. Arch is currently at 3.0.0, but github.io (or the version of Jekyll supported by GitHub) does not yet support it. How did I solve this? That is a story for the next post.