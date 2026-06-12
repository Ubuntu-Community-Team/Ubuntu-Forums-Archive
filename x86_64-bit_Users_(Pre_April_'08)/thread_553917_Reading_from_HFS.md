---
title: "Reading from HFS"
date: 2007-09-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by agilberg on 2007-09-18
Hi there!

I've an HD here wich was used on an G3. I'd like to get some data off it, but somehow I'm stuck. Maybe someone can help. Here we go...

I can mount the HFS-HD with no problem( i.e. no errors) and see all the directories and files, including the correct size of the individual files. But when I try to copy them, Ubuntu can't read the contents of the files. I always get an error and the copied file is 0 bytes.

Syslog tells me an "attempt to access beyond end of device" when a partition (i.e. hdb9) is mounted and an "IO error" when the HD is mounted as a whole (i.e. hdb). Strangely on some occasions with some files it works flawless. Any ideas?

Thanks in advance,

Alex

---

### Post by kidders on 2007-09-19
Hi there,

Looks like the filesystem may be damaged. If I were you, I'd back it up and attempt to repair it. There's any number of reasons you might not succeed though, including physical damage to the disk.

---

