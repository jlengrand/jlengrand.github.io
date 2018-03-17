---
layout: post
status: publish
published: true
title: Merging several SVN repositories into one
author: Julien Lengrand-Lambert
author_login: jlengrand
author_email: julien@lengrand.fr
author_url: https://www.lengrand.fr
categories:
- tips
tags:
- svn
- dev
comments: []
---

The source code at [Spacemetric](https://www.spacemetric.com/) has been split over several reasons for years. The main reason was that some customers were having access to part of our code, while some other parts were to be kept private. This makes working with branches a real nightmare, and we lately decided to merge our repositories back together for this reason.
<br>
The task ahead : Merge 3 different repositories together for a total of around 16k commits, that hold roughly the same structure of folders. One catch though : **It is imperative not to lose the commit history.**
<br>
I looked around on the internet without finding anything really satisfactory. So I ended up rolling my own solution. Here is how I have done it.

### Backing up

The first thing to do is obviously to backup the repositories. You don't want to do anything that is gonna spoil your codebase! **Here, it is important to backup the server side repo, not your local checkout**

On my machine, the repositories are stored in `/spacemetric/svn`, and the repositories that I want to merge are called main, ext-video and public.
<br>
On my machine, this gives us :

    $ cd /spacemetric/svn
    $ svnadmin dump main >  /spacemetric/shared/jll/svnstuff/main_last.dump
    $ svnadmin dump ext-video >  /spacemetric/shared/jll/svnstuff/video_last.dump
    $ svnadmin dump public >  /spacemetric/shared/jll/svnstuff/public_last.dump

And as the main repo is for us the most critical, and I am never sure enough of what I do, I also made a folder copy of the repository :

    $ cp -rp main main_backup

### Creating the new repository

Here, it is worth noting that we decided to create a brand new repository for this, in order to keep the old repositories intact but also to make clear for everybody in a team what happened (by having them making a checkout from scratch).
<br>
As the main repo contains most commits, I decided that I wanted to merge ext-video and public in main. So I started by creating a new repository that was based on the main repo. Which give us :

    $ svnadmin create spacemetric # Creating the new repository
    $ cd spacemetric
    $ svnadmin load . < /spacemetric/shared/jll/svnstuff/main_last.dump # Loading main into the new repo

### Merging repositories

The next step was to insert the content of the ext-video and public repositories into the freshly created spacemetric repo. This is pretty simple to do :
<br>
First we create subfolders for public and video inside spacemetric:

    $ svn mkdir svn+ssh://jll@svn.spacemetric.se/spacemetric/svn/spacemetric/public-repo --message "Added the public-repo folder to merge public repository."
    $ svn mkdir svn+ssh://jll@svn.spacemetric.se/spacemetric/svn/spacemetric/video-repo --message "Added the video-repo folder to merge video repository."

And then load the content of the repository into the subfolders:

    $ svnadmin load . --parent-dir public-repo < /spacemetric/shared/jll/svnstuff/public_last.dump
    $ svnadmin load . --parent-dir video-repo < /spacemetric/shared/jll/svnstuff/video_last.dump

It is interesting to note here that if no commits are lost in this process, **the order and reference of the commits are changed**. In this case, the public commits are rolled on top of the spacemetric commits, and then the video commits are rolled on top of this. Basically, it looks like the video repo has been created last and all commits have been made there one after the other.<br>
The commit history is still complete, but the relative order is now different.

### Cleaning things up

This is close from what I want, but not quite yet. I already said that all my repos have the same structure, so simply having subfolders won't cut it. Ti try to make things simple, here was the situation before the merge:

    - main #SVN repository
      - test
      - spacemetric
      - eclipse
    - video # SVN repository
      - eclipse
    - public # SVN repository
      - eclipse

Here is the current situation :

    - spacemetric # SVN repository
      - test
      - spacemetric
      - eclipse
      - video_repo # subfolder
        - eclipse
      - public_repo # subfolder
        - eclipse

And here is what I want to achieve in the end :

    - spacemetric # SVN repository
      - test
      - spacemetric
      - eclipse # contains the code from main, video and public

Well, the easiest way I found to do this was to do folder operations on the client side. As all repos contained code that was non redundant I was pretty sure there would be no conflict so the process was rather quick and easy. On my local machine, here is what I have done :

    $ svn checkout svn+ssh://jll@svn.spacemetric.se/spacemetric/svn/spacemetric

And then using [Tortoise](https://tortoisesvn.net/) (I hate the SVN command line) I simply moved the eclipse folder from video and public into the main eclipse folder and commited. This was a pretty big and scary commit but everything turned out fine.

### Wrapping up

Last but not least, I made sure everybody has to switch to the new repository by adding a pre-commit hook to the old repositories. Basically, anyone that would attempt to commit would get an error message back. Doing it was pretty simple. In the main, video and public `/hooks/pre-commit` folder I added the following bash script :

    #!/bin/sh
    echo "No more commit here - this is an archive branch. Please use the Spacemetric repository instead." 1>&2
    exit 1

Here it is, a clear, unique repository that will allow developers to start using branches easily without having nightmares!
<br>
The whole process was a bit tedious (16k commits, around 4 hours to do the whole process) and scary, but everything turned out fine and we never looked back.
<br>
My next objective now is to get us to switch from git to svn, as any sane person would do :). Using [git-svn](https://csurs.csr.uky.edu/cgi-bin/man/man2html?1+git-svn) makes my life bareable for now.

<br>
Cheers!

