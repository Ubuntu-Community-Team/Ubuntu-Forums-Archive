---
title: "Using gxine as default audio and video player in firefox"
date: 2006-01-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by xizo on 2006-01-31
Sorry if this is already posted, but I had no luck finding it.  When trying to get a media player such as kaffeine ( kaffeine-mozilla ), mplayer, or totem to work with a 32bit chroot firefox nothing seemed to work automaticly from install, so I decided to find a solution.  This howto is geared towards 64bit users but it will work for 32bit users as well.  If you are a 32bit user just ignore the chroot lingo in steps 1 & 2 and get those programs working in your regular ubuntu environment.

**1)** get firefox and gxine working in 32bit chroot mode

[indent][http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit]("http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+32bit")[/indent]

**2)** install codecs for gxine in 32bit mode if needed

[indent][http://www.ubuntuforums.org/showthread.php?t=75278&highlight=xine+codec]("http://www.ubuntuforums.org/showthread.php?t=75278&highlight=xine+codec")[/indent]

**3)** install mozplugger

[indent]sudo apt-get install mozplugger[/indent]

**4)** remove all unnecessary plugin files from /usr/lib/mozilla-firefox/plugins

[indent]*i.e.* all I have is "flashplayer.xpt,  libflashplayer.so,  mozplugger.so"[/indent]

**5)** replace /etc/mozpluggerrc with [ATTACH]5754[/ATTACH]

[indent]sudo mv **some_directory**/mozpluggerrc.txt /etc/mozpluggerrc[/indent]

**6)** remove .mozilla/firefox/pluginreg.dat from your home directory

[indent]sudo rm ~/.mozilla/firefox/pluginreg.dat[/indent] 

**7)** restart firefox and you should be good to go.


Other than loading media files in a separate window from firefox, this works great.  Let me know if I forgot anything or if you run into any problems with this configuration.


Xizo

---

