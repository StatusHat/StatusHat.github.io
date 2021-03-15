---
title: Theme upgrade (more of a repair, really)
date: 2021-03-15 20:25 +01:00
category: blog
---
Followed the guide more closely this time, and did things a bit more slowly. Here's a step by step:

1. Fetch the blogpost I made from the windows machine

        git pull
        
1. Have a look and see if the blog still works

        bundle exec jekyll serve
        
1. Publish the posts that were hanging around on the linux laptop

        git push
        
1. Create a new branch for working on fixing the theme (to prevent messing up even more)

        git checkout -b theme-upgrade
        
1. Look at the guide. again.

1. Bump the the up to current version by changing the version number in `config.yml`.

1. Rename index.md to index.html. Its contents are still the same, real plain stuff.

1. Create a folder `_data` with the file `navigation.yml`. This is where I define the "main menu" or naviation bar. The format is simple:

        main:
         - title: "Posts"
            url: /year-archive/
         - title: "Categories"
            url: /categories/
         - title: "Tags"
            url: /tags/
         - title: "About"
            url: /about/
            
            
1. Next step is creating the pages I want to be there. They go in the `_pages` folder.

    I already have the "About"-page. It's really not much different from a post with a tad simpler [YAML front matter](https://jekyllrb.com/docs/front-matter/):

        ---
        title: About
        permalink: /about/
        ---

    The pages for posts by year, category and tags are a bit different. I'll see to them next time.

1. Add pagination in `config.yml` like this:
        paginate: 5



