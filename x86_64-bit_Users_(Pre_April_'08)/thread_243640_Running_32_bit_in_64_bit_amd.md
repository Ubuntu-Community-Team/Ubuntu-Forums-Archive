---
title: "Running 32 bit in 64 bit amd"
date: 2006-08-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by mfgobbi on 2006-08-25
I have 2 systems: a 64bit running RedHat EL4 and a 64bit running ububtu. The redhat is great in that it installs and run ANY 32 bit package (x86). The ubuntu, although more user friendly, is becomming a pain in the ***. It won't run firefox 32 bit for example, and I cant install any package that is not what it considers "not the correct architecture".

How can I install a 32 bit version of firefox so I can run java, flash, etc???

Thanks.

m.g.

---

### Post by killkoy on 2006-08-25
Use Kilz's guide for firefox32
[http://www.ubuntuforums.org/showthread.php?p=1174435](http://www.ubuntuforums.org/showthread.php?p=1174435)

---

### Post by Kilz on 2006-08-25
> **mfgobbi said:**
> I have 2 systems: a 64bit running RedHat EL4 and a 64bit running ububtu. The redhat is great in that it installs and run ANY 32 bit package (x86). The ubuntu, although more user friendly, is becomming a pain in the ***. It won't run firefox 32 bit for example, and I cant install any package that is not what it considers "not the correct architecture".

How can I install a 32 bit version of firefox so I can run java, flash, etc???

Thanks.

m.g.

As has been pointed out , use my howto, or install script if you dont want to do it manualy. The reason Redhat and some other distro's can do this is because rpm (the packages readhat uses) is setup to enable multiarch.
Ubuntu is based on Debian, Debian just reciently added the amd64bit archetchure, so they are a little behind. From what I understand it wont be untill the version after edgy untill we see multiarch at the earliest.
That isnt to say amd64 Umbuntu isnt multiarch. The developers have been slowly making improvements towards making the 64bit version multiarch. We can add 32bit packages, but we have to do it manualy. Hopefully things will get better as each release is released.
I know what you are talking about though. It is a pain. My first distro was SuSE, another rpm based distro. I was a little suprised that Ubuntu wasnt multiarch. But the stability, and great feeling of community is more important to me. The setup isnt that hard, and once its done, its done.

---

