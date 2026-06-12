---
title: "Can I run motion in 64 bit?"
date: 2007-12-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by steelmole on 2007-12-08
[Here]("http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome")

Looking at the download page it seems to only have a gutsy version in 32 bit, is there a way to get it to work in a 64 bit install?

---

### Post by Cappy on 2007-12-08
The easiest way would be to install it from the repositories:
```
sudo apt-get install motion
```
or search for it in Synaptic (System-->Administration-->Synaptic Package Manager). The only downside is that it is not the newest version.

Alternatively, You can force install it using ```
dpkg --force-all -i packagename.deb
```
but then you would need to recompile your webcam drivers
[http://ubuntuforums.org/showthread.php?t=634393](http://ubuntuforums.org/showthread.php?t=634393)

Finally, you can compile it from source. I would recommend doing this if you wanted the newest version. If you decide to do this there should be instructions on how to do it in motion-3.2.9.tar.gz

---

