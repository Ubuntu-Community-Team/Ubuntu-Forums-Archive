---
title: "swapping DVD/CD between ubuntu boxes"
date: 2007-03-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by nss0000 on 2007-03-29
Gents:

Figure on watching some home_movies. Seeing as it will be years before DAPPERx64 gets its' own native DVDcodec, I figured I might try swapping the DVD_rw from the U_6.06x64 box over to the U_6.06x32 box --- and swapping the CDrw contrawise. 

Can I  "just do" this , and have the OSs automagically reconfigure for the new hardware?  Or will they spit? 
 And sure, I'd rather swap HW than install software.

nss
******

---

### Post by RS3York on 2007-03-29
If you have home movies, they probably aren't encoded with CSS.  And even if they are, you can get the library to play them on 64-bit Ubuntu.

If you add the following to the bottom of your sources.list file...
```

deb http://www.debian-multimedia.org etch main

```

This can be done in Synaptic/Adept or manually in a text editor by typing the following into a terminal
```

 sudo kate /etc/apt/sources.list

```

Note that I use KDE so I'd use Kate, if you use Gnome then replace "kate" with "gedit".

But once you add that repository and refresh your package manager you'll be able to download and install the "libdvdcss2" package.  *Note: if you live in the United States this package is legally encumbered*  That may be the case in other countries as well.

As for your question about swapping hardware...I don't know.  It should work since the kernel carries all matter of drivers and those drivers don't get discarded just because your machine lacks the hardware.  Turn the computers off first before you swap though :D

I hope that helps.

---

