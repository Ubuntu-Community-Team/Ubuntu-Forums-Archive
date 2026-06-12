---
title: "[SOLVED] No streaming quicktime in 64"
date: 2007-09-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by cwrann on 2007-09-16
I have the feisty version of ubuntu 64 and have recently installed compiz-fusion.
My embedded media files on firefox play very slowly (one frame for every five seconds).
I have all of the necessary plugins and media players.
I have decided that this is either a problem caused by having compiz fusion or by having a 64 bit version of ubuntu or both.
Has anybody else running ubuntu 64 encountered a problem with embedded media files or is this a compiz-fusion problem?

---

### Post by Kilz on 2007-09-16
> **cwrann said:**
> I have the feisty version of ubuntu 64 and have recently installed compiz-fusion.
My embedded media files on firefox play very slowly (one frame for every five seconds).
I have all of the necessary plugins and media players.
I have decided that this is either a problem caused by having compiz fusion or by having a 64 bit version of ubuntu or both.
Has anybody else running ubuntu 64 encountered a problem with embedded media files or is this a compiz-fusion problem?

Its a compiz problem. Desktop effects look cool, But the software is still has a few things it needs to work on. Turn it off temporarily and see if the problem goes away.

---

### Post by cwrann on 2007-09-16
I got rid of compiz fusion and ran 
```
metacity --replace
```
in "run Application" 

I am still having the same video problems.
I have w64 codecs installed in the syntaptic package manager. I am using media player connectivity to try gmplayer, mplayer, and VLC. I have them all set to x11.

Should I completely uninstall all of compiz, even what came with ubuntu? even if I dont have the desktop effects active?

---

### Post by cwrann on 2007-09-16
I also installed the version of swift weasel you offer @ [http://tghc.org/forum/viewtopic.php?pid=4#p4](http://tghc.org/forum/viewtopic.php?pid=4#p4).

when I try to play quicktime in it the browser closes.

---

### Post by Kilz on 2007-09-16
> **cwrann said:**
> I also installed the version of swift weasel you offer @ [http://tghc.org/forum/viewtopic.php?pid=4#p4](http://tghc.org/forum/viewtopic.php?pid=4#p4).

when I try to play quicktime in it the browser closes.

What is in your plugins directory? Please run the following and paste the results.
```
ls -al /usr/lib/mozilla/plugins
```
Also , type ```
about:plugins
``` into the address bar. Copy the quicktime section into a post please.

---

### Post by cwrann on 2007-09-17
Thanks for helping, this has been the hardest nut to crack yet.

```
home@home-desktop:~$ ls -al /usr/lib/mozilla/plugins
total 8460
drwxr-xr-x 2 home home    4096 2007-09-16 20:12 .
drwxr-xr-x 3 root root    4096 2007-04-15 07:58 ..
-r--r--r-- 1 home home     856 2007-06-19 20:31 flashplayer.xpt
lrwxrwxrwx 1 home home      37 2007-08-16 20:57 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
-rwxr-xr-x 1 home home 7040036 2007-06-19 20:31 libflashplayer.so
-rw-r--r-- 1 home home  118744 2007-03-20 05:40 libvlcplugin.so
-rw-r--r-- 1 home home  269216 2007-01-25 19:17 mplayerplug-in-dvx.so
-rw-r--r-- 1 home home     981 2007-01-25 19:17 mplayerplug-in-dvx.xpt
-rw-r--r-- 1 home home  269408 2007-01-25 19:17 mplayerplug-in-qt.so
-rw-r--r-- 1 home home     981 2007-01-25 19:17 mplayerplug-in-qt.xpt
-rw-r--r-- 1 home home  269472 2007-01-25 19:17 mplayerplug-in-rm.so
-rw-r--r-- 1 home home     981 2007-01-25 19:17 mplayerplug-in-rm.xpt
-rw-r--r-- 1 home home  270648 2007-01-25 19:17 mplayerplug-in.so
-rw-r--r-- 1 home home  269760 2007-01-25 19:17 mplayerplug-in-wmp.so
-rw-r--r-- 1 home home     981 2007-01-25 19:17 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 home home     981 2007-01-25 19:17 mplayerplug-in.xpt
-rwx------ 1 home home   70120 2007-09-16 20:12 npwrapper.libflashplayer.so

```


```

MIME Type 	        Description 	                                         Suffixes          Enabled
video/quicktime 	  Quicktime 	                                           mov 	                 Yes
video/x-quicktime 	 Quicktime 	                                          mov 	                Yes
image/x-quicktime 	 Quicktime 	                                         mov 	                Yes
video/quicktime 	   Quicktime 	                                            mp4 	           Yes
video/quicktime    Quicktime - Session Description Protocol 	  sdp 	                 Yes
application/x-quicktimeplayer 	Quicktime 	                             mov 	            Yes
application/smil 	              SMIL 	                                          smil 	                                                                                            yes          
```

---

### Post by Kilz on 2007-09-17
Everything looks ok, but I just wonder, what plugin are you trying to use for quicktime? What is listed as the plugin for it in ```
about:plugins
``` it should be right above what you copied.
Secondly, I wonder if there is some kid of conflict as mplayer and vlc both have the ability to run quicktime video. 
Third, what page are you trying to view the media on?

---

### Post by cwrann on 2007-09-17
Haven't scared you away yet? You've lasted longer than the rest who have tried to help me?

In About:plugins

```
QuickTime Plug-in 6.0 / 7

    File name: mplayerplug-in-qt.so
    mplayerplug-in 3.31

```

I don't think that vlc and mplayer would comflict because I have tried media player connectivity and chosen either one or the other. the browser doesn't close right away but the video plays very slow and choppy and freezes after about 8 seconds.

I am trying to view quicktime files at. apple.com/trailers.

---

### Post by cwrann on 2007-09-21
It looks like I had a couple of things going wrong. I got rid of the VLC plugin, I installed gstreamer gl from synaptic and I got rid of media player connectivity. 
I think that Media Player Connectivity was not allowing the computer to buffer the video clips far enough out to make them watchable, and wasn't saving them in temporary files so that I could wait for the entire clip to load before viewing.
Without Media Player Connectivity the browser was shutting down when I tried to play QT, presumably, because I had VLC selected for quicktime files but mplayer set as the prefered overal media player.
or maybe it was all because I didnt have gstreamer gl installed.
now I wonder what happens when I reinstall compiz fusion...

---

