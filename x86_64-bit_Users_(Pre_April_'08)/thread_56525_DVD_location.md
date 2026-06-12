---
title: "DVD location"
date: 2005-08-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by pailhead on 2005-08-12
Got a stupid question.. I want to check to see if DMA is set on my DVD-Rom. I've got one DVD/RW.  Would it be /dev/dvd? Device manager is showing it as /dev/hdc... 

hope you don't mind the stupid question :)

---

### Post by PeP on 2005-08-12
then it' s /dev/hdc ...

---

### Post by pailhead on 2005-08-12
[QUOTE=PeP]then it' s /dev/hdc ...[/QUOTE]
 Thanks... I just wasn't sure. I thought it would be DVD etc...

Thanks again..

---

### Post by wmcbrine on 2005-08-13
On my system, as perhaps on yours, /dev/dvd is a symlink to /dev/hdc (as is /dev/cdrom). So you could use either.

---

