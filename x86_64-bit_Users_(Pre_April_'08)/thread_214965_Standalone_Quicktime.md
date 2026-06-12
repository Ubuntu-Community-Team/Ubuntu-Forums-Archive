---
title: "Standalone Quicktime?"
date: 2006-07-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-07-13
Yedsterday I missed out on a live webcast about computational linguistics because I was unable to install QuickTime. The instructions are here:

[http://depts.washington.edu/llc/webcast.php]("http://depts.washington.edu/llc/webcast.php")

I have Firefox 1.54 on Dapper-64. About:Plugins says I have Totem-Mozilla plugin, Shockwave, and Java. Totem said the format was not supported. 

I know zero about multimedia. I mean zero. My idea of watching a movie is to go to a theater. Is there any way to watch these things on Dapper-64?

---

### Post by Kilz on 2006-07-13
> **John Jason Jordan said:**
> Yedsterday I missed out on a live webcast about computational linguistics because I was unable to install QuickTime. The instructions are here:

[http://depts.washington.edu/llc/webcast.php]("http://depts.washington.edu/llc/webcast.php")

I have Firefox 1.54 on Dapper-64. About:Plugins says I have Totem-Mozilla plugin, Shockwave, and Java. Totem said the format was not supported. 

I know zero about multimedia. I mean zero. My idea of watching a movie is to go to a theater. Is there any way to watch these things on Dapper-64?

You might want to take a look at my [32bit firefox howto]("http://www.ubuntuforums.org/showthread.php?p=1174435"). You may need to setup 32bit firefox for some plugins. The mplayer plugin on my howto plays quicktime. There is also a automated setup script if you dont want to do it manualy.

---

### Post by timetunnel on 2006-07-13
Actually, I don't know if this applies for 64 bit, but I guess so:
I had best results with the mplayer plugin. Install the following packages, and you should be able to play and stream most formats:

```
libquicktime0
mozilla-mplayer
w32codecs
gestreamer0.10-plugins-good
gestreamer0.10-plugins-bad
gestreamer0.10-plugins-bad-multiverse
gestreamer0.10-plugins-ugly
gestreamer0.10-plugins-ugly-multiverse

```

You'll have to add the following repository in order to get the w32codecs:```

deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
```

Uninstall any other mozilla multimedia plugins. Might conflict with the mplayer plugin

---

### Post by timetunnel on 2006-07-13
Ah, ok, so, according to the howto posted above, my suggestions won't work on a 64 bit system. You always learn :)

---

### Post by Kilz on 2006-07-13
> **timetunnel said:**
> Ah, ok, so, according to the howto posted above, my suggestions won't work on a 64 bit system. You always learn :)
Learning is the best part of running Linux, I try to learn something new each day. :D  For the most part its best to use the 32bit plugins and firefox when dealing with proprietary formats.

---

