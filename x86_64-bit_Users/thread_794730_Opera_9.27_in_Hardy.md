---
title: "Opera 9.27 in Hardy"
date: 2008-05-14
forum: x86 64-bit Users
---

### Post by devosion on 2008-05-14
I just downloaded the .tar.gz file from and attempted sudo ./install.sh in the opera directory after extracting the files. This is the output I received.

> Files will be installed as follows:
-----------------------------------------------------------
 Wrapper Script : /usr/bin
 Binaries       : /usr/lib/opera/9.27-20080331.6
 Plugins        : /usr/lib/opera/plugins
 Shared files   : /usr/share/opera
 Documentation  : /usr/share/doc/opera
 Manual page    : /usr/share/man
-----------------------------------------------------------
Is this correct [ y,n,c | yes,no,cancel ] ?
y

System wide configuration files:
  /etc/opera6rc
  /etc/opera6rc.fixed
 would be ignored if installed with the prefix "/usr".
Do you want to install them in /etc [ y,n | yes,no ] ?
y


When I attempt to run opera from the terminal.

> 
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/9.27-20080331.6/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory


So I know im missing something but im not sure what. And I am unfamiliar how to use the wrapper so I think that could probably be it. I'd appreciate any help in getting it to work. Thanks.

---

### Post by | MM | on 2008-05-15
You need an additional package which is in Ubuntu's repositories.  Install [FONT="Courier New"]libqt3-mt[/FONT]...
```
sudo apt-get install libqt3-mt
```

But tbh the way you have installed Opera is probably not the best.

You should get the debs from [**here**]("http://snapshot.opera.com/unix/snapshot-1962/x86_64-linux/opera_9.50-20080508.2-shared-qt_amd64.deb"), it is the Opera 9.5 beta which is a much better solution on Ubuntu 64bit than Opera 9.27.  There is a native 64bit version (which i linked to), as well 9.5 supports Flash unlike 9.27, plus it introduces a range of new functions which most will agree are great.

[http://www.opera.com/docs/changelogs/linux/950b1/index.dml](http://www.opera.com/docs/changelogs/linux/950b1/index.dml)

---

### Post by Cappy on 2008-05-15
9.5 Beta suffers from frequent crashes (for me at least). I use these stable opera 32-bits. Flash DOES work with them with no extra effort.

To use 9.27 you just need to install getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
and run
```
sudo getlibs /usr/lib/opera/9.27-20080331.6/opera
```

---

### Post by devosion on 2008-05-15
Thanks! 9.5 works great so far.

---

### Post by enyckma on 2008-05-15
[ftp://ftp.opera.com/pub/opera/linux/950b2/final/en/x86_64/](ftp://ftp.opera.com/pub/opera/linux/950b2/final/en/x86_64/)


this is the lates beta of opera for 64 bit version of ubuntu

---

### Post by inphektion on 2008-05-15
> **enyckma said:**
> [ftp://ftp.opera.com/pub/opera/linux/950b2/final/en/x86_64/](ftp://ftp.opera.com/pub/opera/linux/950b2/final/en/x86_64/)


this is the lates beta of opera for 64 bit version of ubuntu

That's beta2.  they've come out with an update after that (rel May 08th) [here.]("http://snapshot.opera.com/unix/snapshot-1962/x86_64-linux/opera_9.50-20080508.2-shared-qt_amd64.deb")
Resolves the following:
**Changelog**
[LIST]
[*]Fix for reloading inline elements.
[*]Fixed cookie settings for local server names.
[*]Fixed forwarding, replying and redirecting of HTML-only mails.
[*]Fixed high CPU usage when subscribed only to the IMAP Inbox folder on GMail.
[*]F8 now works again to focus address field when focus is in panels.
[*][Bug 328318] Wand button is fixed again.
[*]Fixed extensions in File > Save As and File > Open dialogs.
[/LIST]


**UNIX specific:**
[LIST]
[*]Fixed updating of Google Maps when panning
[*]CJK fonts should now look better in the default setup
[/LIST]

---

