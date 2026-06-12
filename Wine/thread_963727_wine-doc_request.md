---
title: "wine-doc request"
date: 2008-10-30
forum: Wine
---

### Post by jorj82 on 2008-10-30
I'm a noob trying to learn.  I want to RTFM but I can't seem to find it, the website's not much help either.  Went here: [http://www.winehq.org/pipermail/wine-users/2005-March/017203.html](http://www.winehq.org/pipermail/wine-users/2005-March/017203.html) 
read this: For starters I would recommend to apt-get winesetuptk if you're not
familiar with the config yet. Then you should apt-get wine-doc and rtfm
at /usr/share/doc/wine-doc (no offense). Because there will be plenty of
situations where you want to change something in your config, so you
might as well get to know the basics.

put this in the terminal: $ sudo apt-get install wine-doc
got this: Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine-doc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  wine
E: Package wine-doc has no installation candidate

So where can I RTFM?  Do I need to add a new repository (I'm just using what is there on install + medibuntu) to get these docs?  Sorry if this is a dumb question but I'm trying to learn.:rolleyes:

edit- almost forgot: hardy heron, wine 1.0

---

### Post by jorj82 on 2008-10-30
After closer examination, I can see that what I was looking at was very old(I rarely look at dates).  I've been searching and reading but I can't find answers.  It might be more productive to just ask the questions.

1- How can I change the resolution wine uses?  I usually keep my desktop at 1024x768, but wine uses 640x480 so fullscreen just looks like a little window with no borders up in the corner.  I can change my desktop to 640x480 to make fullscreen take up the full screen while I use wine, then put it back, but there has to be an easier way.

2- I've installed some games but not all of them show up in the menu.  What's the proper way to make a launcher?  I can make a launcher and point it to the executable but I always get an error trying to use it.

---

### Post by asdfoo on 2008-10-30
> **jorj82 said:**
> After closer examination, I can see that what I was looking at was very old(I rarely look at dates).  I've been searching and reading but I can't find answers.  It might be more productive to just ask the questions.

1- How can I change the resolution wine uses?  I usually keep my desktop at 1024x768, but wine uses 640x480 so fullscreen just looks like a little window with no borders up in the corner.  I can change my desktop to 640x480 to make fullscreen take up the full screen while I use wine, then put it back, but there has to be an easier way.

2- I've installed some games but not all of them show up in the menu.  What's the proper way to make a launcher?  I can make a launcher and point it to the executable but I always get an error trying to use it.

for 1. use winecfg, 2. the launcher has to have exact properties set, look at the other ones for an example

---

### Post by jorj82 on 2008-10-30
OK, so I got the launcher to work.  Thank you!  But I'm still trying to figure out the resolution.  In winecfg I can change the size of the virtual desktop, but my games are still a borderless 640x480 window in the corner of the virtual desktop.  Do I need to edit the registry keys for the actual game or something?  I've read about the registry but I have no idea what I'm doing in there.

---

