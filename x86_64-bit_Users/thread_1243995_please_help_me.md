---
title: "please help me"
date: 2009-08-19
forum: x86 64-bit Users
---

### Post by bubai on 2009-08-19
Hi, I'm totally new in ubuntu. Don't know much about it. I use it mainly for Blender. But yesterday I faced a problem. After running ubuntu some loose connection my system was shutted down. But next time when I boot it says..

GRUB4DOS 0.4.4.2009-04-09, Memory : 639K / 3068M. MenuEnd : 0*434FE[ Minimal 
BASH - like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible completions of a device/filename. ESC at any time exists.]

grub > _

What I'll do. Reinstalling Ubuntu again???:confused:

---

### Post by jwaffolter on 2009-08-19
Reinstalling the system isn't necessary, a grub reinstallation should suffice
Type the following into the grub prompt

root    (hd0,0) 
configfile   /boot/grub/menu.lst

that should boot the system, once logged in open up a terminal
Applications->Accessories->Terminal
and type the following

sudo grub-install /dev/sda

that should fix the problem

---

### Post by bubai on 2009-08-20
Thanks,....I'll try it tonight. Hope it'll solve...

many many thanks..:lolflag:

---

### Post by bubai on 2009-08-21
:confused::confused::confused:
No.....

I can't belive that it didn't help me. After putting
configfile /boot/grub/menu.lst command

it says
error 15. file doesn't found.

What I need to do....:confused:

---

### Post by jwaffolter on 2009-08-21
enter the root line just as before

then type

kernel     /boot/vmlinux<kernel-version>   root=/dev/sda1 ro
initrd       /boot/initrd.img<kernel-version>

(replace <kernel-version> with the kernel ver string, if you dont know it just hit tab after typing the vmlinux and initrd.img)

and finally type boot

---

