---
title: "ATI x700 on 64-bit Hardy 8.04"
date: 2008-05-23
forum: x86 64-bit Users
---

### Post by TheFella on 2008-05-23
I've been searching the forums for solutions to this, but I've actually come up with too many and I'm not too sure what to try, and in what order!

Here are my specs:

Acer Ferrari 64-bit
ATI x700 mobility
Ubuntu 8.04 fresh install

I can't post up the xorg.conf at the minute, as I'm in work and not on my laptop.


To install the graphics card, I ticked the restricted drivers box and that was it. I can use the desktop effects, but the computer is very slow and when I try to watch something, like VLC or Zattoo, it flickers a lot. When I turn off the advanced effects, videos work fine.

So, I was wondering what to try first? Should I check the 
```
Driver "fglrx"
```
in the xorg.conf config and then run 
```
sudo aticonfig --initial -f
``` ??

Should I go to [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html) and follow the instructions there, as it's a pretty recent release?

There's also this guide:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)


Sorry for asking about this, as it's been done to death, but that's part of my problem; information overload!

---

### Post by TheFella on 2008-05-28
Anyone?

---

### Post by Kilz on 2008-05-28
> **TheFella said:**
> Anyone?

I would recommend the howto you linked to above using method 2.

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

