---
title: "w64codecs real formats, xine instead of mplayer"
date: 2007-05-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by idtt2s on 2007-05-27
I have installed mplayer and w64codecs, which allows me to play real formats on my 64-bit system. However, I would much rather use kaffeine to play my videos instead of mplayer. But if I link xine to the directory that i THINK has the real codecs (/usr/lib64/win32/), it would instantly crash whenever I try to open a video without producing a valid backtrace. Does anyone have any suggestions?

---

### Post by david_2001 on 2007-05-27
> **idtt2s said:**
> I have installed mplayer and w64codecs, which allows me to play real formats on my 64-bit system. However, I would much rather use kaffeine to play my videos instead of mplayer. But if I link xine to the directory that i THINK has the real codecs (/usr/lib64/win32/), it would instantly crash whenever I try to open a video without producing a valid backtrace. Does anyone have any suggestions?
The files are installed in /usr/lib/codcs and /usr/lib64/win32 is a symbolic link to /usr/lib/codecs, so it shouldn't make any difference which of the two is specified as the path to RealPlayer codecs in Xine or Kaffeine.  Howover, a little searching indicates that the real problem is a bug in xine-lib.  Take a look at [https://launchpad.net/ubuntu/+source/amarok/+bug/91500](https://launchpad.net/ubuntu/+source/amarok/+bug/91500).

---

### Post by idtt2s on 2007-05-28
Sorry, I don't find a working solution in the link you gave me. Also, from what I gather, the people in that link were using a 32-bit system. I know for a face xine can play real formats on 64-bit, since it works on Gentoo. But on Ubuntu I just don't seem to get it working.

---

### Post by Kilz on 2007-05-28
You might want to bookmark the sticky posts in this section. [This one is the most important. ]("http://ubuntuforums.org/showthread.php?t=191205") It will give you information on installing the few 32bit applications you will need in 64bit land. The thread is old, but the information is still good.
Find the Mplayer and m32codecs link and use it. That is , unless you want to install about 50 packages manualy.
There is no such thing as m64codecs. The name means m= Microsoft, 32 = 32 bit files, = codecs =you know what they do.

---

### Post by david_2001 on 2007-05-29
> **Kilz said:**
> 
Find the Mplayer and m32codecs link and use it. That is , unless you want to install about 50 packages manualy.
There is no such thing as m64codecs. The name means m= Microsoft, 32 = 32 bit files, = codecs =you know what they do.
But there is a package called **w64**codecs!  I have it installed, it includes codecs that allow real video to be played and certainly works with 64-bit mplayer (I prove this to myself almost every day by watching video news items on the BBC website using the 64-bit mplayer plugin for 64-bit firefox).  Check out the [COLOR="DarkOrange"][Medibuntu]("http://medibuntu.sos-sts.com/index.php")[/COLOR] repository.

PS. The fix for xine-lib didn't work for me either but I was less concerned because I use mplayer for playing real media.  EDIT: The mplayer plugin will play all of the test clips at [http://service.real.com/realplayer/test/](http://service.real.com/realplayer/test/), I just checked.

---

