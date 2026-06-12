---
title: "Flash plugin stops working after upgrade to firefox 3"
date: 2008-06-13
forum: x86 64-bit Users
---

### Post by hari_seldon99 on 2008-06-13
Hi all,

 Running kubuntu hardy heron x86_64 on my core2 duo. I installed firefox some weeks back and the flashplugin-nonfree, ubufox etc. and everything was working fine. Now I upgrade to firefox 3 from the repos and I cannot see the flash plugin in about:config


running firefox from shell and trying to see about:config shows the following errors


```

   Unknown option on the command line: --info
   Error parsing option on the command line: --info
   GCJ PLUGIN: thread 0x6228d0: NP_GetMIMEDescription
   GCJ PLUGIN: thread 0x6228d0: NP_GetMIMEDescription return
   GCJ PLUGIN: thread 0x6228d0: NP_GetValue
   GCJ PLUGIN: thread 0x6228d0: NP_GetValue: returning plugin name.
  GCJ PLUGIN: thread 0x6228d0: NP_GetValue return
   GCJ PLUGIN: thread 0x6228d0: NP_GetValue
   GCJ PLUGIN: thread 0x6228d0: NP_GetValue: returning plugin description.
  GCJ PLUGIN: thread 0x6228d0: NP_GetValue return

```

The output of about:plugins is provided here:

[http://pastebin.com/m28717b07](http://pastebin.com/m28717b07)


The output of nspluginwrapper -l is:
```

/usr/lib/mozilla/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5
/usr/lib64/mozilla/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5
/usr/lib/firefox/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5
/usr/lib64/firefox/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-nonfree/libflashplayer.so
  Wrapper version string: 0.9.91.5

```

All the plugins are still there in /usr/lib/mozilla/plugins

ls -l /usr/lib/mozilla/plugins shows
```

lrwxrwxrwx 1 root root     37 2008-06-13 12:36 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
-rw-r--r-- 1 root root 290880 2008-05-13 05:31 mplayerplug-in-dvx.so
-rw-r--r-- 1 root root   1067 2008-05-13 05:31 mplayerplug-in-dvx.xpt
-rw-r--r-- 1 root root 290880 2008-05-13 05:31 mplayerplug-in-qt.so
-rw-r--r-- 1 root root   1067 2008-05-13 05:31 mplayerplug-in-qt.xpt
-rw-r--r-- 1 root root 290880 2008-05-13 05:31 mplayerplug-in-rm.so
-rw-r--r-- 1 root root   1067 2008-05-13 05:31 mplayerplug-in-rm.xpt
-rw-r--r-- 1 root root 290872 2008-05-13 05:31 mplayerplug-in.so
-rw-r--r-- 1 root root 290880 2008-05-13 05:31 mplayerplug-in-wmp.so
-rw-r--r-- 1 root root   1067 2008-05-13 05:31 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 root root   1067 2008-05-13 05:31 mplayerplug-in.xpt

```


Despite all this, flash plugin doesn;t work, nor does it even show up in about:config

Trying to see a flash video or something on ff3 leads to a popup for installing the required plugins, which then leads to a "flashplugin-nonfree already installed" message (removing flashplugin-nonfree) and getting the ff3 dialog to install it changes nothing, I still can;t get flash to work.

I'd greatly appreciate any advice on how to fix this.
Thanks for your attention.
Regards.

---

### Post by Sef on 2008-06-14
Have you read [Kliz's tutorial]("http://ubuntuforums.org/showthread.php?t=772490")?

---

### Post by hari_seldon99 on 2008-06-14
> **Sef said:**
> Have you read [Kliz's tutorial]("http://ubuntuforums.org/showthread.php?t=772490")?

I have. It says "If flash still does not work DO Not install the scripts below.". Well it didn't. I wasn't sure whether I should post there so I  started another thread.

Update: I ran the Getflash script in Kliz's tutorial. No luck, same problem. I ran ff3 from shell and got the following error when typing about:plugins

```

Unknown option on the command line: --info
Error parsing option on the command line: --info

```

with no flash plugin displayed., even though both libflashplayer.so and npwrapper.libflashplayer.so are there in /usr/lib/mozilla/plugins and npwrapper.libflashplayer.so is symlinked from /usr/lib/firefox-addons/plugins

---

