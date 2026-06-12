---
title: "Canon Pixma iP1600 not working"
date: 2008-05-01
forum: x86 64-bit Users
---

### Post by pcchynoweth on 2008-05-01
Hi everyone:

I've dabbled in Linux off and on for several years. Took the plunge and installed Hardy on my relatively new Acer AMD laptop. My experience has been pretty good so far with one major exception, and right now that is preventing me from using ubuntu. I can't use the printer. I've done a lot of checking and I think the issue is 64 bit drivers for Canon printers. It seems to be confirmed by the comment on this page:

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview)

Any ideas on how to make my printer work? It shows up in the list of printers. I tried installing it again, and after trying to install (using a few different procedures I found online), the printer makes noises as if it is being accessed, but I can't print anything.

Thanks in advance for any advice you can give...

Peter

---

### Post by glefty on 2008-05-01
You can try force installing the 32 bit libraries, I did that to be able to use my MP-610 on AMD64.  If you have the drivers already, half the work is done.

Here's a link that'll point you in the right direction on the force install.

[http://ubuntuforums.org/showthread.php?t=723113&highlight=Force](http://ubuntuforums.org/showthread.php?t=723113&highlight=Force)

Good Luck!!

---

### Post by pcchynoweth on 2008-05-01
Thanks glefty! That looks promising. I also found this thread, and while I haven't tried it, it also looks like it will work. I'll try it and report back.

[http://ubuntuforums.org/showthread.php?t=593414](http://ubuntuforums.org/showthread.php?t=593414)

---

### Post by old_geekster on 2008-05-01
I have a Canon MP610.  I was running Hardy 64-bit, but couldn't get my printer installed.  So, since I had done an upgrade from Gutsy, I decided to do a clean install.  I turned on my printer before doing the install.  I believe this is the trick to getting Hardy to recognize it.  I don't have everything functioning perfectly, but I can print.

Oh, by the way, I am using Hardy 32-bit at present.  The same procedure worked with it also.

---

### Post by glefty on 2008-05-02
I'm using my MP-610 as a network printer attached to a WD Netcenter, so THAT made it a little more fun :).  I just go local, or memory card if I need to scan anything.

---

### Post by pcchynoweth on 2008-05-02
After close to a full day of working on it, I have something coming from the printer. I think there are still some issues, but at least it is printing for me. 

The answer was to apply changes as described in my previous post along with the one suggested by glefty. I tried so many different things, that it's hard to nail down exactly what made it work, but I think the answer is this:

I followed the steps in this post:
[URL="http://ubuntuforums.org/showpost.php?p=4767724&postcount=10"]
http://ubuntuforums.org/showpost.php?p=4767724&postcount=10[/URL]

Of course, he was installing an iP1500 and I was working on an iP1600. The drivers for an iP1600 are the same as iP2200. They can be found on the Canon European site:

[http://software.canon-europe.com/files/soft24301/software/iP2200_Linux_260.tar.gz]("http://software.canon-europe.com/files/soft24301/software/iP2200_Linux_260.tar.gz")

Everything worked as the above link described until this:

```
bjfilterpixmaip1500
```

The commands are quite different for the 1600/2200. Look in /usr/local/bin to see what they are. When you try them, you get a confusing error message "file or command not found" (or something like that)

The trick was to use the getlibs command to fix the dependencies in all the associated commands in /usr/local/bin

There was one final problem, namely a requirement for libtiff.so.3 

This was fixed by symbolically linking libtiff.so.3 to libtiff.so.4 in /usr/lib32

I think more tweaking of the ppd file in /usr/share/cups/model will make the printer work even better.

I probably would have given up today if I had not tried the Turboprint free driver. That proved it could work, so I went back and hacked away a bit more until it was working. 

BTW, for any other Newbies out there, the CUPS console at:[http://localhost:631]("http://localhost:631") is a good thing to know about.

Hope this helps others!

---

### Post by ken78724 on 2008-11-13
Many thanks.... what is written for CanonPixmal1500 on [https://wiki.ubuntu.com/CanonPixmaIP1500](https://wiki.ubuntu.com/CanonPixmaIP1500) may solve my need to print. Glad to see this help. But at the moment I can't follow the steps and make it all work.

---

