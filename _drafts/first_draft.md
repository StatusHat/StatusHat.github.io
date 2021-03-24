---
title: Another day another fumble
---

    $ git checkout master
    $ git merge theme-upgrade
    $ bundle exec jekyll serve
    $ git push origin master
    
# So what is the plan(s) for next time?

 1. Check last post for stuff to address

 1.   Add pages for posts by year, category and tags

    Fixed here: _data/navigation.yml

 1. Figure out what’s up with the apostrophes around the file name for the “branches and breakage” post in the output of ls _posts command earlier
 1. Read slowly and carefully
 1. Take notes ALL the time, both while reading and of every change and command. Maybe I’ll finally learn something. Or at least finally learn…
 1. Don’t use the IDE (VS Code) for things that can be done on the command line before
        you know how those things work
        you know how the IDE works

1. And maybe also get vim (neovim, actually) working as editor in VS Code. Or take a pause from VS Code and just use vim for a while. Those things might also be the subject for upcoming posts.

1. Also: Increase the post width. It's cramped
    
    Fixed here: index.html
    
    
Things I also learned:

* Non-commited changes can be commited from any branch. Well at least non-added changes. Need to check again. Just make sure you check branch status before committing
* Jekyll can keep a "draft post" folder. Handy! Create folder _drafts and stuff your drafts and work in progress there. To test, serve your site with the --drafts flag. 
