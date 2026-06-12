---
title: "I think I found a bug involving f-spot ..."
date: 2008-01-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by linuxgrrl on 2008-01-16
when I select "fullscreen," either with F11 or the menu button, sometimes it works correctly but most of the time it does the following:
1. loses focus on the main window, and 
2. appears to create a second window called "fullscreen" which it then minimizes to the taskbar.  I can right-click and close this other window, but trying to maximize it has no effect.

This bug is seemingly not the same as the other fullscreen problems reported w/ F-spot, which all seem to involve Compiz.  I have not installed compiz as far as I know.

I reported my little problem to Launchpad and added the terminal output (see [https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/181501](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/181501)) .  The bug is marked "incomplete," and I'm not sure what that means (I've never done this before), but I bet it would be useful if anyone else could say whether this happens to them.

So, anyone else with  gutsy 64 l who has experienced this?  I imported a photos database from dapper -- I've been adding to it for years, thousands of tagged photos and would really like to get it working properly.
Mary

---

### Post by NightwishFan on 2008-01-25
I have this same problem. I do not know if it is just a 64bit problem or 32 personally. I am going to look into this a bit now.

---

### Post by linuxgrrl on 2008-02-19
I'm glad it's not just me.  If you could add your experience to the Launchpad bug, that would be great.  I'm not sure what else I need to do to get attention for this problem.

EDIT: Ok, turns out it's not actually a bug .. in F-spot, anyway.  F-spot requires that you use something called a "compositing" window manager in order for fullscreen to work properly.  The default installation of Gutsy uses Gnome with a window manager called "Metacity" which is not compositing.  To fix the problem, you can install Compiz (resource-heavy) or if you are resource constrained, do what I did, and replace metacity with xfwm4 while keeping gnome. It took me a while to figure this one out ... I'm perplexed that the stock installation of gutsy includes f-spot if it won't work without this kind of tweaking.  It's a pretty obvious usability problem if you ask me. Oh well.

---

