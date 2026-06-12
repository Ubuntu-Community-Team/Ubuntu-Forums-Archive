---
title: "DVD burning software"
date: 2007-04-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by sammyd253 on 2007-04-02
Currently on my Windows XP setup I use the combination of AnyDVD and CloneDVD to make backups of my DVD's.  Is there anything like this available in Ubuntu?  Also, will it work in a 64-bit environment?


Thanks in advance!

---

### Post by bruenig on 2007-04-02
Perhaps [xdvdshrink]("http://dvdshrink.sourceforge.net/").

---

### Post by kuja on 2007-04-02
> **sammyd253 said:**
> Currently on my Windows XP setup I use the combination of AnyDVD and CloneDVD to make backups of my DVD's.  Is there anything like this available in Ubuntu?  Also, will it work in a 64-bit environment?


Thanks in advance!
There are certainly a variety of things around for backing up and/or burning dvds. Not only will things work in a 64-bit environment, it should also perform significantly better.

---

### Post by Kilz on 2007-04-02
k9copy is a good application, and k3b will copy a lot of dvd's. They are both kde applications, but will work with gnome.

---

### Post by FrozenFOXX on 2007-04-02
I gave k3b a shot but surprisingly it just flat-out didn't work.  It would make copies but either the video stream was trashed or more commonly just flat out wouldn't run and die silently.

I highly recommend K3B for burning, didn't know it could copy them.  I'm currently trying out DVD Shrink through Wine (0.9.34) and it's going...slowly, but going.

---

### Post by stchman on 2007-04-02
> **FrozenFOXX said:**
> I gave k3b a shot but surprisingly it just flat-out didn't work.  It would make copies but either the video stream was trashed or more commonly just flat out wouldn't run and die silently.

I highly recommend K3B for burning, didn't know it could copy them.  I'm currently trying out DVD Shrink through Wine (0.9.34) and it's going...slowly, but going.

You need to install the CSS decryption for Ubuntu.  I have ripped encrypted DVDs with Ubuntu many times (archival purposes).

My website will tell you how:

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

Using k9copy will decrypt the DVD and k3b will then be able to burn the .iso.

---

