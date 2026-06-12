---
title: "ImageWriter will not write write img"
date: 2009-05-28
forum: x86 64-bit Users
---

### Post by Linux Kelley on 2009-05-28
To all,

I am trying to use ImageWriter to write to my thumbdrive but all it does is unmount it.

Image: /home/kelley/Downloads/Linux Distros/ubuntu-9.04-netbook-remix-i386.img
Target Device: HP v100w (/dev/sdf)
Unmounting all partitions of /dev/sdf:
Trying to unmount /dev/sdf1...
/dev/sdf1 successfully unmounted


Thanks,

Kelley

---

### Post by Adam Fitton on 2009-09-17
Yeah I just had the same problem after years!

I think it was from having the Image deep in a file structure. Move the img file closer to root. I put it on my desktop and it worked fine for me then.

---

