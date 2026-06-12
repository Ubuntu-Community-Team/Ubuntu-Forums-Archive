---
title: "gnofin"
date: 2006-03-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by maury on 2006-03-16
Has anyone managed to get gnofin ( a small checkbook manager) to run on the AMD_64  version. That is the only thing keeping me from using ubuntu as my primary system. I have downloaded it from the debian site but it dosen't open.  TIA. maury
PS I have been able to install and run it on mandrake, mepis,fedora and pure debian  I am using mepis now but would like to run 64 bit. Everything else is working great but I hate to have to swap out my drive just to make a checkbook entry. (removeable drive bay).

---

### Post by jklasdf on 2006-03-17
[QUOTE=maury]I have downloaded it from the debian site but it dosen't open.  [/QUOTE]
It seems to be working for me. Are there any errors given when you try to open it?

---

### Post by maury on 2006-03-18
This is the message I get
"Could not open "gnofin_0.8.4-2.2_amd64.deb

Archive type not supported"
Sorry for the late reply. I have to go out again but will be back shortly

---

### Post by jklasdf on 2006-03-23
Open a terminal, go to the directory where gnofin is, and type:
sudo dpkg --install gnofin_0.8.4-2.2_amd64.deb
and hit enter.

---

### Post by jklasdf on 2006-03-23
Alternatively, if you don't want to use the terminal, and have kPackage installed, you can use that. Open kpackage, click File->Open, then browse to gnofin, open it, and hit install.

---

