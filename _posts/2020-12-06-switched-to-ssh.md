---
layout: post
title: Do one thing or do no things at all
date:   2020-11-22 18:06 +0100
categories: fumbling update 
---
It's been slow going for some time. I keep falling down some wiki rabbithole or being distracted by some maybe cool thing to try, and ending up getting nothing done. So I finally managed to focus on just one thing for long enough that I managed to do at least one thing...
# Logging in is hard to do
It took me about two pushes to get sick of inputing my GitHub password every time I made a change to this page. My password on GitHub is long and  difficult to remember. Not designed for muscle memory. So I looked in to caching, keyrings, and ways to be lazy while still sort of secure. 

At first I felt like I was stumbling about like a blind person. The first articles I found suggested I use a personal token. After quite some reading, I finally gave up. It seems the only real change that would give me was having another difficult string to input every time I wanted to interact with my GitHub repos.

I could maybe have found a way to include the token in a keyring and have it looked up when I wanted to login, but by then I was tired of it all and did other stuff for a week or so. I almost felt like giving up

## But breaking up is harder
I kept reading and trying to figure this stuff out, but it kept eluding me. Maybe I wasn't cut out for this stuff. Maybe I'm to old and tired to learn new shit.

But even so, I am a geek at heart and every now and then I did a little search and did a little reading. And then, at last, I stumbled across a suggestion for authenticating with SSH. That sounded much more like what I wanted. And I really didn't want to quit quite yet.

The process was simple. Generate an ssh-key locally, which was automatically added to my keyring, paste the key into the proper text field in my GitHub settings and update my remotes from https to SSH:

    $ git remote set-url origin git@github.com:USERNAME/REPOSITORY.git
    
Finally! Every time I push a change, I can use my local finger friendly password. Add to that some caching, like for an example to remember my login for an hour:

    $ git config --global credential.helper 'cache --timeout=3600'

and now I can get stuff done with a lot less hassle.

# In other news
I have been having slowdowns and DNS timeouts at home lately, so I looked into alternatives to my ISPs designated resolver.

Google supplies a fast, free lookup service through 8.8.8.8, but I'd like to not give them any more data than I already do.

Reading around some more, it seems Cloudflare has been pushing a free, fast and privacy aware DNS lookup service at 1.1.1.1 for a couple of years. Its privacy track record seems good and their policy seems at once top notch and sincere. The fact that they employ independendt auditors to keep them to their word adds up a decent level of trustworthiness. I gave them a try.

So far, I have yet to be hugely impressed. I do trust them still, but while some of my issues are solved, new ones have been introduced. Might be  a follow up on this in the future.


