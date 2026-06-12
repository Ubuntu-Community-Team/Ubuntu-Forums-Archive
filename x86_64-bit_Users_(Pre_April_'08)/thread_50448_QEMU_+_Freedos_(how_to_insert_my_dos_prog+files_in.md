---
title: "QEMU + Freedos (how to insert my dos prog+files into it?)"
date: 2005-07-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by yansen on 2005-07-20
hi,

wanna ask again..

after install Qemu and use it with freedos image download from [http://fabrice.bellard.free.fr/qemu/freedos.img.bz2](http://fabrice.bellard.free.fr/qemu/freedos.img.bz2) , wat i wanna do is get my dos program + files into the freedos image ( C: in Qemu), so i can run my dos prog, how can i do it? 

i've tried googling, but since i'm newbie in linux, i still can't find the way.

btw, i run the freedos by passing the autoexec.bat (with press F5) since if not, when i execute the dir command, it says
> Volume in drive C has no label
File not found.

thanks,
yansen

---

### Post by filterban on 2005-07-20
[QUOTE=yansen]hi,

wanna ask again..

after install Qemu and use it with freedos image download from [http://fabrice.bellard.free.fr/qemu/freedos.img.bz2](http://fabrice.bellard.free.fr/qemu/freedos.img.bz2) , wat i wanna do is get my dos program + files into the freedos image ( C: in Qemu), so i can run my dos prog, how can i do it? 

i've tried googling, but since i'm newbie in linux, i still can't find the way.

btw, i run the freedos by passing the autoexec.bat (with press F5) since if not, when i execute the dir command, it says


thanks,
yansen[/QUOTE]

Honestly, I have never used Qemu.  Looks like a virtual machine, though.  I don't think this is a Hoary and/or AMD64 question - perhaps you should post in the QEMU or Freedos forums instead.

---

### Post by yansen on 2005-07-20
[QUOTE=filterban]Honestly, I have never used Qemu.  Looks like a virtual machine, though.  I don't think this is a Hoary and/or AMD64 question - perhaps you should post in the QEMU or Freedos forums instead.[/QUOTE]

Thanks for your suggestion, i will gonna try it  :)

---

### Post by derjames on 2006-09-27
Hi there, 
what you have to do is to create an aditional virtual drive based on a linux directory, put all your stuff there, run your virtual machine and freeDOS will be able to see your MS-DOS/FreeDOS files

for example type

qemu freedos.img -hdb fat:/home/james/Virtual/disk1

this tells QEMU to boot from the virtual drive called freedos.img and creating and aditional drive (D:>) based on the linux directory
/home/james/Virtual/disk1  (which you create of course)

now copy all your stuff onto this folder, once on FreeDOS
type D: and press enter and you will be able to see its content

Hope this helps

Cheers

---

### Post by derjames on 2006-09-27
By the way see attached picture, Doom running under Ubuntu 6.06 using QEMU+FreeDOS.

Cheers

---

