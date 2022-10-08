---
title: Theme upgrade (more of a repair, really)
date: 2021-03-15 # 22:52 +01:00
category: blog
tags:
  - git
  - rtfm
  - jekyll
  - theme
---

Time to start doing things properly. Or try to, at least. I followed [the guide](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/) more closely this time, and did things a tiny bit more slowly. Here's a walkthrough in 10 steps (You gullible sod... ed.):

<!--more-->

1.  Fetch the blogpost I made from the windows machine

        $ git pull

1.  Have a look and see if the blog still works

        $ bundle exec jekyll serve

1.  Publish the posts that were hanging around on the linux laptop

        $ git push

1.  Create a new branch for working on fixing the theme (to prevent messing up even more)

        $ git checkout -b theme-upgrade

1.  Look at the guide. Again.

1.  Bump the the theme up to current version by changing the version number in `config.yml`.

1.  Rename `index.md` to `index.html`. Its contents are still the same, real plain stuff:

        ---
        layout: home
        author_profile: true
        ---

1.  Create a folder `_data` with the file `navigation.yml`. This is where I define the "main menu" or navigation bar. Without this, the Blog is really nothing but a list of posts. The format is simple:

        main:
         - title: "Posts"
            url: /year-archive/
         - title: "Categories"
            url: /categories/
         - title: "Tags"
            url: /tags/
         - title: "About"
            url: /about/

1.  Next step is creating the pages I want to be there. They go in the `_pages` folder.

    I already have the "About"-page. It's really not much different from a post with a tad simpler [YAML front matter](https://jekyllrb.com/docs/front-matter/):

        ---
        title: About
        permalink: /about/
        ---

    The pages for posts by year, category and tags are a bit different. I'll see to them next time.

1.  Oh, and add pagination in `config.yml` so the front page doesn't end up indefinitely long. Like this:

        paginate: 5

And then I noticed. where did the post "Cross platform blorging" from last time go? I forgot to see if it was pulled in, and I forgot to look for it when I verified that the blog still worked in step 2. Well, it sure isn't on the new branch. Is it still on `master`, at least? Let's find out!

    $ git checkout master
    $ ls _posts
    2020-11-22-first-post.md        2020-12-17-new-theme.md     2021-03-15-theme-upgrade.md
    2020-12-06-switched-to-ssh.md   2021-03-02-cross-platform-blorging.md
    2020-12-10-excerpts.md         '2021-03-04-branches and breakage.md'

Yup. That can't be good. So what happened here? I messed something up when trying to pull and merge. I _thought_ I was doing what I wrote in steps nr. 1-3, but I actually _let VS Code do it for me_ with the Sync command in the Source Control tab. And I'm not quite sure it does things the way I think it does. Let's try to fix this from the command line proper. (And stop lying _to myself_, sole purveyor of this blog, in the posts, maybe.).

While I'm not anywhere close to properly understanding how git branches, pulls, pushes and merges work, this is a fairly small project and I'm confident I can manage to undo whatever mess I make trying to bring things together again. With a little help from the Interweb pixies, of course. And yes, where was I? Command line:

    $ git checkout theme-update
    $ git pull origin master
    hint: Pulling without specifying how to reconcile divergent branches is
    hint: discouraged. You can squelch this message by running one of the following
    hint: commands sometime before your next pull:
    hint:
    hint:   git config pull.rebase false  # merge (the default strategy)
    hint:   git config pull.rebase true   # rebase
    hint:   git config pull.ff only       # fast-forward only
    hint:
    hint: You can replace "git config" with "git config --global" to set a default
    hint: preference for all repositories. You can also pass --rebase, --no-rebase,
    hint: or --ff-only on the command line to override the configured default per
    hint: invocation.
    From github.com:/StatusHat/StatusHat.github.io
    * branch            master     -> FETCH_HEAD
    Merge made by the 'recursive' strategy.
    _posts/2021-03-02-cross-platform-blorging.md | 12 ++++++++++++
    1 file changed, 12 insertions(+)
    create mode 100644 _posts/2021-03-02-cross-platform-blorging.md

That actually seemed to work. 1 file changed. The 12 insertions are just the lines in that file. But note that git itself tells me I'm probably not doing this properly. Specify merge strategy, is more or less what the hint-part says. Oh well, I did some [short reading](https://www.atlassian.com/git/tutorials/syncing/git-pull) on the difference between merge and rebase, and it doesn't really matter in my use case. Main difference is how git deals with commit history. For shared projects or bigger (and more important) work, this would probably matter a lot. But here we are. What's "fast-forward only", you say? Don't ask... I guess we'll get there eventually.

What I did specify this time was where to pull from and where to pull to. I _think_ that was what was supposed to happen all the way back at the top as well, but here we are. Note to self: Use `$ git status` all the time so you know what's going on. That way it will at least be apparent which branch is active...

One thing that doesn't really show in the last command line paste is the interactive part of the pull and merge. I thought I would get some sort of summary of what would be changed, but I couldn't see any. Maybe I'm still going too fast. Anyway, I was prompted for a commit message and that was it. It worked, and all that is left to do is merging this branch back into master and pushing it back up online.

Oh no you don't! First we take this for another spin locally to see if it works:

    $ bundle exec jekyll serve

So what is the plan(s) for next time?

1. Add pages for posts by year, category and tags
1. Figure out what's up with the apostrophes around the file name for the "branches and breakage" post in the output of `ls _posts` command earlier
1. Read slowly and carefully
1. Take notes ALL the time, both while reading and of _every_ change and command. Maybe I'll finally learn something. Or at least finally _learn_...
1. Don't use the IDE (VS Code) for things that can be done on the command line before
   1. you know how those things work
   1. you know how the IDE works

And maybe also get vim (neovim, actually) working as editor in VS Code. Or take a pause from VS Code and just use vim for a while. Those things might also be the subject for upcoming posts.

Bedtime!
