---
title: "Juk crashes"
date: 2006-02-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by ubuntubrian on 2006-02-27
I'm unable to get Juk to ruh although it was fine. I installed some new themes with synaptic as well as MPlayer plug-ins. Perhaps this is the problem though it shouldn't be. Here's the terminal output of the error:

@ubuntu:~$ juk
kbuildsycoca running...
DCOP aborting (delayed) call from 'anonymous-27711' to 'juk'
juk: ERROR: Communication problem with juk, it probably crashed.
brianokeefe@ubuntu:~$ X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x3800142
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
KCrash: Application 'juk' crashing...

---

### Post by svref on 2006-02-27
er, I can't find any package named "juk", and freshmeat.net provides no search results, so maybe you could specify a bit better what you're talking about so people don't have to be detectives to help you.

---

### Post by ssam on 2006-02-27
its one of the kde music players [http://developer.kde.org/~wheeler/juk.html](http://developer.kde.org/~wheeler/juk.html)

you should probably file a bug at [https://launchpad.net/malone](https://launchpad.net/malone)

---

### Post by ubuntubrian on 2006-02-28
An update on the issue: Amarok now crashes also as do kgpg and xmms. xmms from the terminal:
Gtk-WARNING **: Unable to locate loadable module in module_path: "libsmooth.so",
Message: device: default
Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 1540 error_code 8 request_code 72 minor_code 0
Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 1541 error_code 8 request_code 72 minor_code 0

I haven't checked every app but it seems to be kde oriented and a KDE session does not allow the theme to be changed. I should say I can change the theme in the Kcontrol but ntohing happens.

---

