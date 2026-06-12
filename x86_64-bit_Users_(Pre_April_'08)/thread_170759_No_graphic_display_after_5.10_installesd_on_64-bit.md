---
title: "No graphic display after 5.10 installesd on 64-bit."
date: 2006-05-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by sidy on 2006-05-05
Hello there,

After the second time I've installed ubuntu 5.10 on my 64bit-PC, (2 hdds, 80 as master and 40 as sleve), the instalation has been done on 40 (all my datas are in the 80).

Then, in stead of go to login happened the following:


'biiiiiiiiiiiiiiiiiiiiiii! biiiii! biiiii! bii!' sound,
and
a black screen with a little line like this   ' - ' on the left-top-corner. nothing else!


from here I cannot go any where, unless a press the power bottom, which is not right, then I can go through the 'recovery mode' and access the root.


Aditional information, 
On root to get access to the 80hdd, came up the following error:

'(nautilus:6535): GTK-Warning **:cannot open display'

After I had done the following:

mount
cd /mnt
ls
mkdir hda1
ls
mkdir hda2
ls
mkdir hda3
ls
mount /dev/hda1 /mnt/hda1
mount /dev/hda2 /mnt/hda2
mount /dev/hda3 /mnt/hda3
cd hda2
ls
cd home
ls
nautilus

(nautilus:6535): GTK-Warning **:cannot open display.

CAN YOU PLEASE SEND ME COMMANDS OF HOW CAN I DISPLAY?

By the way, I've used the live cd, is the same problem.

Regards.

Sidney.

---

### Post by mips on 2006-05-05
It's not acceptable behaviour to double or triple post.

Please don't respond to this thread, rather respond to this one [http://www.ubuntuforums.org/showthread.php?t=170756](http://www.ubuntuforums.org/showthread.php?t=170756)

---

