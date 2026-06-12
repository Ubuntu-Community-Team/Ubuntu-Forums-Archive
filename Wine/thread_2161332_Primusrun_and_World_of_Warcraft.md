---
title: "Primusrun and World of Warcraft"
date: 2013-07-10
forum: Wine
---

### Post by Akkaid on 2013-07-10
Hey yall,

Im very new to Linux, running Ubuntu 13.04 64bit.  Like alot of folks, I want to make sure I can run a game or two before I go hook, line and sinker for Ubuntu.  So far, I have installed WoW with Wine 1.6, got Bumblebee and Primus, and I can run the game with low settings getting about 43fps.  Honestly, this is good enough, but I want to see if I can perfect it.

I have read every WoW related post that comes up in google for the past 6 months, and they have gotten me this far.  Now my issue is with Primus, and most of the posts related to Primus are writted to folks with MUCH greater knowledge of Ubuntu than this guy.  So, if anyone has the time, I'd appreciate a little hand holding here-

System-
MSI X460 Laptop, Ubuntu 13.04
Nvidia 630M Graphics, 2GB 
8GB RAM
Wine 1.6


What I have done so far-

installed the stuff via Winetricks that all the 'how tos' told me to.
Changed the config.wtf to use OpenGL vice D3D
launched the game 3 or 4 different ways, this is the one I am trying to get to work now-
    [COLOR=#000000][FONT=verdana, arial, sans-serif][SIZE=1]blank_mode=0 LD_PRELOAD="libpthread.so.0 libGL.so.1" __GL_THREADED_OPTIMIZATIONS=1 [COLOR=#444444][FONT=UbuntuRegular, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]optirun -b primus[/SIZE][/FONT][/COLOR] [COLOR=#444444][FONT=UbuntuRegular, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]wine [/SIZE][/FONT][/COLOR][COLOR=#444444][FONT=UbuntuRegular, Ubuntu, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif][SIZE=2]/home/jake/Documents/World\ of\ Warcraft/wow-64.exe

It gives me a list of errors, but it seems they are a bit long to post here....and Im not smart enough to know how to give yall access to the log.  I saw something about a patch for Primus to fix this issue, but I have no idea how to use it, it was just a bunch of script in a box.  Hope yall dont mind helping a linux idiot, really starting to love this OS.  Just tell me what to do and Ill get it done!
[/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR]

---

