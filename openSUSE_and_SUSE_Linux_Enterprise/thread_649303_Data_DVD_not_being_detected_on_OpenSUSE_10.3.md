---
title: "Data DVD not being detected on OpenSUSE 10.3"
date: 2007-12-24
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Moonfrost on 2007-12-24
I inserted a "data DVD" which I made more than half a year ago and it's what I use when some OS related issue happens and I have to fresh re-install...all my music and pictures are there...the problem is that every single LInux distro recognized it perfectly but OpenSUSE 10.3 tells me that it's write-protected and it's not allowed to show it's contents...is there any fix for this? because only for that reason alone (the music mostly) I would switch to another distro right away...I'm guessing that it can't be the DVD codecs I need since those are for "DVD-Video" right? I might be mistaken though...not an expert here...

EDIT: I installed all the necessary codecs from packman repo etc etc. and it still will tell me that my data DVD is "write proctected"? could anybody help me?

EDIT #2: I installed all plugins and such from the packman repositories and followed these instructions

```
http://www.softwareinreview.com/linux_optimizations/hacking_opensuse_10.3.html
```

but even after all that Data DVD won't be read (I haven't tried DVD video playback) and .mp3 files still won't play because programs like Amarok and such tell me "codec not found" or something to that effect...

EDIT #3: This is the error I get

```
mount: block device /dev/sr0 is write-protected, mounting read-only mount: wrong fs type, bad option, bad superblock on /dev/sr0, missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg | tail or so
```

---

### Post by RedDwarf on 2007-12-25
> **Moonfrost said:**
> because only for that reason alone (the music mostly) I would switch to another distro right away...
...or you can help openSUSE reporting the bug: [http://bugzilla.novell.com/](http://bugzilla.novell.com/)
You probably should include your "/etc/fstab" and a detailed description of your DVD structure (ISO9660? UDF? multi-session? etc.). And _obviously_ you should include your syslog (you should have included it here) since "In some cases useful info is found" there.

An obvious workaround is to mount that DVD manually. If you know the filesystem type... And no, this hasn't anything to do with codecs.

---

### Post by Moonfrost on 2007-12-25
> **RedDwarf said:**
> ...or you can help openSUSE reporting the bug: [http://bugzilla.novell.com/](http://bugzilla.novell.com/)
You probably should include your "/etc/fstab" and a detailed description of your DVD structure (ISO9660? UDF? multi-session? etc.). And _obviously_ you should include your syslog (you should have included it here) since "In some cases useful info is found" there.

An obvious workaround is to mount that DVD manually. If you know the filesystem type... And no, this hasn't anything to do with codecs.

I'm pretty sure it's multi-session since I'm able to write to it as long as I want (as long as there's still free space on the DVD)...that's why it's called a "data disc" on in this case "data dvd" to be more specific...

EDIT: Ubuntu, Windows, and like 3 other Linux distros I tried all read the data perfectly...so I thought it was probably some kind of library or codec...?

---

