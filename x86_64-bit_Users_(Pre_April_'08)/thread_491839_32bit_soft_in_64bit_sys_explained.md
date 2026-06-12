---
title: "32bit soft in 64bit sys explained?"
date: 2007-07-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by kzm. on 2007-07-04
i am no guru on linux really, i just followed the how-tos for wine and skype and flash... but i was wondering if there is are good sites that explains how to make 32bit software usable for the 64bit system for merely morons like me? so i would be able to come up with solutions by myself.. if thats possible at all.

---

### Post by John.Michael.Kane on 2007-07-04
It's not about being a  guru on linux, and theres no one way to do it theres no one way to explain it either, As theres many ways to get 32bit running under 64bit, and It's up to you which method your comfortable using.

First you should always see if the source is available for you to compile before resorting to mix libs.

For the most part all you need to install the ia32-libs,and the programs dependencies. 

Usually when you sudo aptitude install 32 bit program x it will spit out a msg saying what lib's or dependencies. are not met it may even tell you that it can't run on 64bit at all in which case you would have to find a work around. 

One way may be through use of a chroot setup. [http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+setup](http://ubuntuforums.org/showthread.php?t=24575&highlight=chroot+setup)

Heres how debian explains things.
[http://www.debian-administration.org/articles/534](http://www.debian-administration.org/articles/534).
[http://www.debian-administration.org/articles/531](http://www.debian-administration.org/articles/531)
[https://alioth.debian.org/docman/view.php/30192/21/debian-amd64-howto.html](https://alioth.debian.org/docman/view.php/30192/21/debian-amd64-howto.html)

The other way provided the program/programs install with out issue is through the use of bash scripting the install.  Which is what most of the scripts of the scripts used to install programs in the section are based on. 

One note: With each ubuntu increase you have to factor in the each ubuntu version move eg: 7.04 to 7.10 that 32bit program x that installed with say four dependents using 7.04 may now require six under 7.10. so you will have to add them to your script as well.

Your also going to do some reading theres no escaping that, As I said everyones method will be different, and may not fit the way you want to do things.

---

