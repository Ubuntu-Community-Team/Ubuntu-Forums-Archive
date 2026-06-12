---
title: "Cant use dvdrip"
date: 2005-11-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by switi on 2005-11-03
Hi!

I tried to benchmark my new Athlon64 X2 and installed dvdrip.
apt-get install dvdrip went fine and could retrieve all dependencies.

Well but the application is not usable. dvdrip messages:
nemo:~$ dvdrip
sh: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory

And the dvdrip gui shows that it cannot find any of the necessary tools.

It works in the 32 Bit chroot environment.

Thanks for help,

Switi

---

### Post by teaker1s on 2005-11-03
make sure all dependencies are installed like 'libdvdread'

---

### Post by switi on 2005-11-03
I am sure that I have. I think dvdrip is unable to load the needed shared libraries. Currently I try to compile it on my own.

Solution:
[http://lists.debian.org/debian-amd64/2005/05/msg00867.html](http://lists.debian.org/debian-amd64/2005/05/msg00867.html)

So you simply have to disable the "Workaround transcode NPTL
bugs" switch in the preferences, as explained in the 2005/05/17
entry on [http://www.exit1.org/dvdrip](http://www.exit1.org/dvdrip).

---

### Post by Drain on 2005-11-19
[QUOTE=switi]I am sure that I have. I think dvdrip is unable to load the needed shared libraries. Currently I try to compile it on my own.

Solution:
[http://lists.debian.org/debian-amd64/2005/05/msg00867.html](http://lists.debian.org/debian-amd64/2005/05/msg00867.html)

So you simply have to disable the "Workaround transcode NPTL
bugs" switch in the preferences, as explained in the 2005/05/17
entry on [http://www.exit1.org/dvdrip](http://www.exit1.org/dvdrip).[/QUOTE]

Thanks for the help there - I had been searching for the answer to that problem for a few hours before I ran into the answer here. :-)

---

### Post by ryan76 on 2006-11-23
Can someone please explain to me how to do this? I couldn't find that entry on [http://www.exit1.org/dvdrip](http://www.exit1.org/dvdrip) and I'm not a perl programmer.

Thanks

edit: No worries, I found the way to install on 64-bit [here]("http://ubuntuforums.org/showthread.php?t=191205&highlight=dvdrip").

---

