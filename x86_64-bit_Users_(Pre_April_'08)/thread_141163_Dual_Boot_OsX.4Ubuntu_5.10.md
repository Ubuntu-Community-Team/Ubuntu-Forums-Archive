---
title: "Dual Boot OsX.4/Ubuntu 5.10"
date: 2006-03-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by g12345567 on 2006-03-07
I have just setup my older G3/400 B&W Powermac With a dual boot OS X.4 and Ubuntu 5.10. Both seem to be running/booting successfully without a problem. 

My setup is as follows

HD1: 20gb  Ubuntu 5.10 and Yaboot.
HD2: 120gb Mac OS X.4.

The problem is when I boot into OS X.4 I get the following message displayed on the screen. "disk insertion. The disk you inserted was not readable.  Initialize,  Ignore,  Eject"

According to OSX.4 HD1 is configured as "Apple Partition Scheme" with Apple Unix partitions 

When I installed Ubuntu 5.10 I told the installer to Delete all partitions on HD1 and use automatic partitioning scheme.

Has the installer used the correct partitioning scheme or would I need to go back and reinstall the Ubuntu to fix this up so the linux partions are recognised by OS X.4 in my dual boot setup. Any ideas to resolve this would be greatfull.

---

### Post by ssam on 2006-03-07
you need to install this [http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/) in mac os x to be able to read linux partitions.

---

### Post by Ptero-4 on 2006-03-07
That's odd. OS X shouldn't even notice the linux disk at all.

---

### Post by engla on 2006-03-07
[QUOTE=ssam]you need to install this [http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/) in mac os x to be able to read linux partitions.[/QUOTE]
Nope, that doesn't work at all in OSX v10.4 [sadly]

I say this -- if you don't depend on Tiger, use OS X v10.3 Panther together with ubuntu, so you can use ext2/3 disks and other sane stuff.

---

### Post by ssam on 2006-03-08
[QUOTE=engla]Nope, that doesn't work at all in OSX v10.4 [sadly]
[/QUOTE]

is this still true? it looks like there is a new version that is begining to work in tiger. maybe the development could be sped up by use of the guys amazon wishlish.

---

### Post by engla on 2006-03-08
[QUOTE=ssam]is this still true? it looks like there is a new version that is begining to work in tiger. maybe the development could be sped up by use of the guys amazon wishlish.[/QUOTE]
Well, I don't know.. last time I tried was around 3 weeks ago, but it looked pretty dark when I researched it then. In panther I thought the solution with ext2fs was robust, and I was able to have my osx home on an ext2 partition.

Please post if you find anything indicating progress though, I'm very interested..

---

### Post by g12345567 on 2006-03-09
[QUOTE=ssam]you need to install this [http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/) in mac os x to be able to read linux partitions.[/QUOTE]

Thanks for the above. Os 10.4 now recognises my Linux ubuntu partition. No more unrecognised hard disk partitions. And even give me R/W access to the hard disk.

---

