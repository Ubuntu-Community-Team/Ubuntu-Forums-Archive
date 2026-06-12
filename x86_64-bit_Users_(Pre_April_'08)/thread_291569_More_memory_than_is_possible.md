---
title: "More memory than is possible"
date: 2006-11-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by v79 on 2006-11-02
I'm copying some files from a windows NTFS partition to a virtual windows folder in vmplayer, right. Incredibly slowly, reporting 2.5hrs to copy 10Mb.
Anyway, the system was a bit sluggish so I opened up Gnome System Monitor. See the attached screenshot.

Apparently, Gnome, Nautilus, Firefox and Rythmbox are using...

17179869180.0GiB

Which is rather a lot. 171,7986,9180.0 GiB = 171 Petabytes? On my 1Gb RAM machine. Possible bug in System Monitor?

Anyone else manage to beat 171 Petabytes on Ubuntu?

[IMG]http://www.liamjdavison.info/Screenshot-System%20Monitor.png[/IMG]

---

### Post by kuja on 2006-11-02
No, I think you're the new record holder :D

---

### Post by bigbyte on 2007-12-14
it is 16 exabytes (18.44 if you prefer base 10).

---

### Post by UnrealMiniMe on 2007-12-14
No wonder people are starting to think Gnome is getting bloated!  ;)
Too bad you took the shot down...that would've been cool to see!

---

### Post by nutz on 2007-12-15
Ha! You should put the screenshot back up.

---

### Post by exoren22 on 2007-12-15
Yes, I get this too, and I think we should file bug reports on launchpad. 
Clearly something is causing the numbers to stick on the maximum, because my total ram used is 476.3MiB, with no swap used.

---

