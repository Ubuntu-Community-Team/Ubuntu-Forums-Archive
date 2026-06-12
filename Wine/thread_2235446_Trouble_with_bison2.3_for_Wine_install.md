---
title: "Trouble with bison2.3 for Wine install"
date: 2014-07-21
forum: Wine
---

### Post by alan35 on 2014-07-21
OK, this is a long and round a bout post...

I have an older stand a lone (no Internet) emachine 733i that I am using to try and pull files off an old SCSI MAC HD.
I installed Ubuntu 8.10 from CD. I need to get Wine working to run Foxpro on the machine to try to use the files in the old SCSI drive, if I can get them copied to the IDE drive. 

I installed m4-1.4.3 everything went OK. I installed Flex-2.5.33 everything went OK. I installed bison-2.3 and I get an error...
Make:***No rule to make Target 'm4/bison-i18n.m4.'needed by Makefile' Stop.  There are very few posts about this and one from a programming forum saying the Target file is missing.

What I tried to do was use files that are about the same age, hoping there would not be any version problems.
I suspect I may have some sort of version problem.
I know I am reaching back a long time in peoples memories, but any suggestions would be great.

Thanks  alan

---

### Post by alan35 on 2014-07-23
I ended up installing m4-1.4.13 and then Bison-2.4.2 and flex-2.5.35. I then went through the three wine versions and tried them all.
1.1.1 complains about xlib/xfree86 and FrontForge and won't complete the install. 0.9.49 seemed to install, but when I launch wine it gives me an error while loading shared libraries it can't find libwine.so.1.
0.9.19 complains about dlls in makefile.in and doesn't complete the install.

With 0.9.49 I can see the libwine.so.1 in the folder, not sure why it doesn't see it. I wonder if its not in the right place. 
Does anyone know the path to libwine.so.1?

I downloaded a couple more versions to try 0.9.56 and 1.1.24 and try them tomorrow.

---

