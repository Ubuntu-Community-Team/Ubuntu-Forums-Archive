---
title: "how do you boot xp and ubuntu from a menu"
date: 2007-12-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by soratheultima on 2007-12-12
well hi im new to this forum since i want to have both windows  xp and Ubuntu 7.10 on my computer
i have tried this one booter called boot-NG  that didnt work 
ive tryed it about 4 times now and im getting pissed i have one sata drive and one ide
can any one tell me how to boot them on a menu without downloading any thing
or give me a program

---

### Post by Existentialist on 2007-12-12
Ubuntu comes with a bootloader called GRUB.  Have you installed Ubuntu yet?  When you do it should install GRUB to the MBR of the drive you install it to and it will see your windows install also.  You might need to go in to BIOS and change the primary boot hard drive to the one you installed Ubuntu on.

---

### Post by soratheultima on 2007-12-12
but i also have xp alreadz installed so yeah thanks ill try if works

---

### Post by azbarcea on 2007-12-17
take a look at this thread:
[http://ubuntuforums.org/showthread.php?t=56723](http://ubuntuforums.org/showthread.php?t=56723)

if you want a solution that will just work for you, please specify:
 1. all your hardisks and partitions and its mount points
```

$ sudo df

```
 2. groub vs lilo (if u don't know what this is ... then forget about this line)
 3. How your menu u want to look like


this link might also help you: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
:-)

---

