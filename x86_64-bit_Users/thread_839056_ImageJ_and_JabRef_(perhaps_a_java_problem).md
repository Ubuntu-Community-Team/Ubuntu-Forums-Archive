---
title: "ImageJ and JabRef (perhaps a java problem)"
date: 2008-06-24
forum: x86 64-bit Users
---

### Post by pstickar on 2008-06-24
Hi,

while using JabRef or ImageJ, opening new (child) windows usually leads to blank windows with no content. After several retrials the window appears with its content, as expected. Of course, retrying several times is annoying. Whether pictures or just a couple of buttons with a text is irrelevant. The problem does seem to be linked to a particular set of widgets. Sometimes a couple of repetitions suffices. Some other times as many as 20 retrials are needed.

I'm writting in this forum because I did not see any reference to the problem in the other forums, so I guess that only a minority of users do experience this problem, if at all. I use to have the same problem with Ubuntu-7.10. After a fresh install (and new versions of both JabRef and ImageJ) the problem presists.

JabRef was installed using aptitude, ImageJ was manually downloaded/installed.

Any help/tip/piece of advice will be highly appretiated.

Regards,
p.

PS. uname -a:
Linux laptop 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64 GNU/Linux

---

### Post by pixel :-) on 2008-06-26
What java did you installed.What version did you installed? 

64 bit java
sun-java6-bin 

32bit java
ia32-sun-java6-bin

free/opensource implimentation
icedtea 

experiment between them,experiment between versions if nescaisery,32bit should work best.No need to install and uninstall every time.With this you can reconfigure witch one your system should use.
sudo update-alternatives --config java

---

### Post by pstickar on 2008-06-28
pixel:-),

thank you for your answer.
Regarding imageJ, the free/opensource implementation works the best, by far.
In the case of jabref, all three give blank (child) windows very often.

I have not seen any difference between 32 and 64 bit java for either jabref or imagej. Both perform poorly. This is surprising because in the web site of jabref, they recommend sun-java.

Your simple approach to reconfigure is awsome.

Cheers,
p.

---

