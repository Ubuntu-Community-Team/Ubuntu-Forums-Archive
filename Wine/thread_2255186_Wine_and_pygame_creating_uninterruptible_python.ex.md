---
title: "Wine and pygame creating uninterruptible python.exe process"
date: 2014-12-02
forum: Wine
---

### Post by tcll5850 on 2014-12-02
just wanted to post something I'm rather annoyed about as this happens quite often with a particular game I'm working on which has the same setup as another program I'm working on that has no problems.
the only difference is I'm using a game engine called pyggel which is wrapped around pygame.

I'm using python portable 2.7.6.1 on wine 1.7.30 x64 with an x86 prefix on Ubuntu 14.04

the game runs just fine but after closing the window, the python.exe process becomes uninterruptible where the parent process is 'init'

I took this issue up here, where I was told this was a kernel bug:
[http://askubuntu.com/questions/555927/how-do-i-terminate-uninterruptible-and-zombie-processes?noredirect=1#comment763470_555927](http://askubuntu.com/questions/555927/how-do-i-terminate-uninterruptible-and-zombie-processes?noredirect=1#comment763470_555927)

I'm a real noob to Ubuntu so I'm not sure if this is an issue with Wine...
in any case, I have to restart my compy to fix it.


I'm told hibernation also works here, but my system freezes upon resume and I never get back to the desktop.

for more info there I can provide my MBD specs and GFX card if needed. :)


EDIT:
oh btw, sorry if this is in the wrong area, or I should be posting this somewhere else entirely.

figured it out and wrote down the issue here:
[http://code.google.com/p/pyggel/issues/detail?id=18&thanks=18&ts=1417581074](http://code.google.com/p/pyggel/issues/detail?id=18&thanks=18&ts=1417581074)

it may be something with wine and improper termination in pygame

EDIT:
excuse the D-post btw, I felt it needed to be separated.

---

