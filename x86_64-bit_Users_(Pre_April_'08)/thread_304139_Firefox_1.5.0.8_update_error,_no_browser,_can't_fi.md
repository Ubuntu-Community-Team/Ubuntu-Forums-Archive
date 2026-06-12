---
title: "Firefox 1.5.0.8 update error, no browser, can't fix"
date: 2006-11-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by zafo on 2006-11-21
I have an AMD 64X distribution of Ubuntu 6.06LTS.  Automatic Software Update is running and this morning an update from Firefox 1.5.0.7 to 1.5.0.8 was ready, so I clicked to install it.  It had installation errors ("Error Broken Count > 0")and now Software Update won't work and neither will Firefox (I am having to resort to using IE6 running under Crossover to send this message).

I followed instructions to use apt-get install -f and ran into several errors:
```
rod@rod-amd-linux:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  firefox
Suggested packages:
  latex-xft-fonts libthai0
The following packages will be upgraded:
  firefox
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/9420kB of archives.
After unpacking 24.6kB of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: unable to initialize frontend: Kde
debconf: (Unable to load Qt -- is libqt-perl installed?)
debconf: falling back to frontend: Dialog
(Reading database ... 114510 files and directories currently installed.)
Preparing to replace firefox 1.5.dfsg+1.5.0.7-ubuntu0.6.06 (using .../firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_amd64.deb) ...
Unpacking replacement firefox ...
dpkg: error processing /var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/mozilla-firefox', which is also in package kaffeine-mozilla
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I am not quite sure what to do and I haven't been able to find any other forum or web entry of people with similar problems.  If you have any ideas please let me know.

Thanks

---

### Post by mvaniersel on 2006-11-21
I noticed this message in your log:
> 
 trying to overwrite `/usr/lib/mozilla-firefox', which is also in package kaffeine-mozilla

Have you tried uninstalling kaffeine-mozilla first? It might help.

---

### Post by zafo on 2006-11-21
I am a little leery about uninstalling kaffeine-mozilla as Synaptic Package Manager says it will also remove firefox-gnome-support and ubuntu-desktop. If I am being overly cautious please let me know, but those sound like things I don't want to delete.

Rod

---

### Post by zafo on 2006-11-21
Mea Culpa!  I was looking at the wrong program when I posted those other removals.  I removed mozilla-kaffeine and the update went through and I have both Firefox and the Update Manager working again.

Thanks - good call!

Rod:D

---

