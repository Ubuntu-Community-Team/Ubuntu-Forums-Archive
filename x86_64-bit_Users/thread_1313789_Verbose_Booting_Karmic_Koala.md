---
title: "Verbose Booting Karmic Koala"
date: 2009-11-04
forum: x86 64-bit Users
---

### Post by King of Heart 4711 on 2009-11-04
Hello, I don't know if this has been answered yet or not, searched the forums and can't find it. Is there any way that I can make 9.10 verbose boot? Not the biggest fan of splash screen. I know it maybe a stupid question, but I just cant figure it out. Any help is much appreciated.

---

### Post by iruel on 2009-11-04
you can edit in filenamed **/boot/grub/grub.cfg**
and search the kernel image you want boot, and change this value
[B][I]set quite=1
[/I][/B]to[B][I]
set quite=0[/I][/B]

and remove "quite" text on your kernel image,
***linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sda5 ro quiet splash***
to
***linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sda5 ro splash***      << this is if you want still use splash but with verbose message
***linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sda5 ro                 ***<<****this line is if you only show verbose message
**** and if you want choose kernel image before usplash screen,increase **timeout 0** to **timeout 5**

;)

---

### Post by sanderj on 2009-11-04
> **iruel said:**
> you can edit in filenamed **/boot/grub/grub.cfg**
and search the kernel image you want boot, and change this value
[B][I]set quite=1
[/I][/B]to[B][I]
set quite=0[/I][/B]

and remove "quite" text on your kernel image,
***linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sda5 ro quiet splash***
to
***linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sda5 ro splash***      << this is if you want still use splash but with verbose message
***linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sda5 ro                 ***<<****this line is if you only show verbose message
**** and if you want choose kernel image before usplash screen,increase **timeout 0** to **timeout 5**

;)

quite, or quiet ... ?

Anyway: remove "quiet" and "splash" from the boot options by pressing F4 or F6 (can't remember) in the grub menu.

HTH

---

### Post by iruel on 2009-11-04
> **sanderj said:**
> quite, or quiet ... ?

Anyway: remove "quiet" and "splash" from the boot options by pressing F4 or F6 (can't remember) in the grub menu.

HTH
it's **quiet, **so it's like[B] set quiet=0
[/B]sorry for mistakes,

if you from fresh install, and you just only has one OS, you can't pressed any button,because by default the grub **timeout** is **0**, and this is to fast.
so you must set the **timeout** first.

and if you has two or OS,you can press **F2** for kernel image, and then press **"e**" or "**E**" on the option;)

---

