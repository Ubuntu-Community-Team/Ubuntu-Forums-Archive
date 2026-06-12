---
title: "OpenOffice Printing Problems"
date: 2007-02-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Pseudo-Morph on 2007-02-27
After recently purchasing a new printer (Samsung ML-2571N) I have discovered that I have problems printing from within OpenOffice, all other applications print correctly as do documents sent to the printer from Windows boxes, leading me to believe the issue lies with how OO.o sends documents to the printer. Documents sent to the printer from within OO.o are spooled and reported as printing correctly however the pages produced only have the bottom left  1/4 of the page displayed within OO.o printed within the top right corner of an otherwise blank page. At first glance it would appear that the printer margins have been set correctly however from within OO.o all printing settings appear to be correct.

A large amount of time spent on the OO.o forums, Ubuntu forums and googling have produced little result except a mention this one about a similar problem that has inflicted a number of other users of OO.o 2.0.4 [http://www.oooforum.org/forum/viewtopic.phtml?t=46051](http://www.oooforum.org/forum/viewtopic.phtml?t=46051)

At this point in time I cannot confirm if this problem is restricted to OO.o 2.0.4 as I have not been able to install alternate versions of OO.o to see if the problem exists in those. One thing I have noticed is that one document forwarded to me by a MS Office user has printed correctly, all documets produced in earlier versions of OO.o along with .rtf documents I routinely use at university do not.

My questions are as follows, has anyone else had the same or a similar problem with OO.o? Is there a way to install OO.o without using the offical Ubuntu repos to a 64 bit system? Does anyone know where I can find an earlier version of OO.o (say 1.0.3) that might solve this issue.

---

### Post by Pseudo-Morph on 2007-03-06
Bump?

---

### Post by John Jason Jordan on 2007-03-06
> **Pseudo-Morph said:**
> My questions are as follows, has anyone else had the same or a similar problem with OO.o? Is there a way to install OO.o without using the offical Ubuntu repos to a 64 bit system? Does anyone know where I can find an earlier version of OO.o (say 1.0.3) that might solve this issue.
I suspect it won't help, but you can install 2.1 on Edgy amd64. I posted about where to find the .debs here:

[http://ubuntuforums.org/showthread.php?t=360847](http://ubuntuforums.org/showthread.php?t=360847)

I can't remember where, but there are also OOo 2.0.2 for amd64 somewhere on Ubuntu. I never tried them because I discovered that my problem was in Ubuntu Edgy 1md64, not in OOo. I proved this by running the Edgy amd64 live/install CD -- problem continued -- but when I used the 32-bit Edgy live/install CD the problem disappeared. But my problem had nothing to do with printing.

---

### Post by mrfreddy on 2007-03-06
> **Pseudo-Morph said:**
> Is there a way to install OO.o without using the offical Ubuntu repos to a 64 bit system? Does anyone know where I can find an earlier version of OO.o (say 1.0.3) that might solve this issue.

Not sure about earlier stuff but I use this mirror:[http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/]("http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/")

for upcoming x86_86 stuff. Have a look through that site you may find something in the stable directory.

If you do find something you want to install then remove your existing debs first with:
```
sudo apt-get remove $(dpkg -l | grep openoffice.org | awk '{print $2}'| sed -e :a -e '$!N;s/\n/ /;ta' -e 'P;D')
```

copy the deb.tar.gz into /tmp & install
```
cd /tmp/
tar xvzf  OOo_2.2.0_LinuxX86-64_install_en-US_deb.tar.gz
cd DEBS
dpkg -i *.deb
```

Good luck.

---

