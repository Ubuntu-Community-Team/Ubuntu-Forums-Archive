---
title: "Video Resolution"
date: 2006-01-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by bkv2k on 2006-01-21
I just loaded ubuntu for the AMD64 and it went unbelievably well.  When asked to set my video resolution, I managed to hit Return before I got a couple of higher resolutions set.  Is there an easy way, without reloading the operating system, to add these to the Video Selections in the Screen Resolution preferences?

---

### Post by happyponcho42 on 2006-01-21
Ah, this seems to be a common issue with Ubuntu installs.  Check out [this](http://ubuntuforums.org/showpost.php?p=454217&postcount=1) for the fix.

---

### Post by bkv2k on 2006-01-21
[QUOTE=happyponcho42]Ah, this seems to be a common issue with Ubuntu installs.  Check out [this](http://ubuntuforums.org/showpost.php?p=454217&postcount=1) for the fix.[/QUOTE]

Thanks for the help.  I'll give this a try.

---

### Post by Fallen Guru on 2006-01-21
$ sudo dpkg-reconfigure xserver-xorg

should ask you the xserver configuration questions again.

---

