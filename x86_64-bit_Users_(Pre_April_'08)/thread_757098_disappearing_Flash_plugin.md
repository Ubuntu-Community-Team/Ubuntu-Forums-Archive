---
title: "disappearing Flash plugin"
date: 2008-04-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by akahige on 2008-04-16
Not sure if this is related to the script, so I started a new thread...

Been beating my head against getting Flash installed on AMD64 Gutsy for awhile now. Found the sticky thread at the top of this forum and that worked remarkably well.

While everything works fine when it works, I am still having a problem that I was having before -- Flash, for lack of a better word, just disappears every so often. Nothing crashes, Firefox just acts like Flash was never installed. Nothing in particular seems to trigger this behavior, and it comes back when I restart Firefox -- but I'd rather not have to do that all the time.

Anyone ever see this, or have any ideas...


Here's the requested command dump:


```

 ls -al /usr/lib/mozilla//plugins/
total 6876
-rwxr-xr-x 1 michael users 7040036 2007-06-19 17:31 libflashplayer.so
lrwxrwxrwx 1 michael users      39 2008-03-01 11:32 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 michael users      48 2008-04-16 09:39 mozilla-tiff-plugin.so -> ../../mozilla-tiff-plugin/mozilla-tiff-plugin.so
lrwxrwxrwx 1 michael users      60 2008-04-16 10:49 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

```


```

 ls -al /usr/lib/firefox/plugins/
total 16
lrwxrwxrwx 1 michael users    39 2008-03-01 11:32 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
-rw-r--r-- 1 michael users 11456 2008-03-25 08:19 libunixprintplugin.so
lrwxrwxrwx 1 michael users    48 2008-04-16 09:39 mozilla-tiff-plugin.so -> ../../mozilla-tiff-plugin/mozilla-tiff-plugin.so
lrwxrwxrwx 1 michael users    60 2008-04-16 10:49 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

```


```

uname -a
Linux RGO-vserver 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux

```


Running Firefox 2.0.0.13 on Ubuntu 7.10, with the r48 version of the Flash installer script.

---

