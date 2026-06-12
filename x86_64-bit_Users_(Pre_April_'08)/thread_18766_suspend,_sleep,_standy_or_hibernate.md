---
title: "suspend, sleep, standy or hibernate"
date: 2005-03-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by blinksilver on 2005-03-08
anyone have anything of that nature working on their 64 bit system, my laptop would be very thankful,

---

### Post by blinksilver on 2005-03-08
what, come on no one owns a 64bit laptop, someone must have tried,

---

### Post by Pse on 2005-03-09
Why don't you try it? I don't think it'd be risky for your system.

---

### Post by blinksilver on 2005-03-09
i am more then willing,  but i have no idea where to being, have looked through the forum for some help but have a hard time finding something that will do me good, make a suggestion and i will run with it

---

### Post by kubla on 2005-03-09
[QUOTE=blinksilver]i am more then willing,  but i have no idea where to being, have looked through the forum for some help but have a hard time finding something that will do me good, make a suggestion and i will run with it[/QUOTE]
 I've not yet had a chance to try but under the 2.4 kernel and my old toshiba laptops, I used apm.

Actually, in the case of my Toshibas, I'd just close the lid and they'd suspend and I'd open them and they'd wake up. They could also be suspended manually by issuing the command: apm -s

I'm crazily busy today but from a quick check and typing "apm" I get back: No APM support in kernel

Now, this could be because apm has changed in the 2.6 series or because, indeed, the stock ubuntu kernel doesn't the apm modules included... will experiment more this weekend but if anyone else has any insights...

---

### Post by Johan on 2005-03-09
[QUOTE=kubla]I've not yet had a chance to try but under the 2.4 kernel and my old toshiba laptops, I used apm.

Actually, in the case of my Toshibas, I'd just close the lid and they'd suspend and I'd open them and they'd wake up. They could also be suspended manually by issuing the command: apm -s

I'm crazily busy today but from a quick check and typing "apm" I get back: No APM support in kernel

Now, this could be because apm has changed in the 2.6 series or because, indeed, the stock ubuntu kernel doesn't the apm modules included... will experiment more this weekend but if anyone else has any insights...[/QUOTE]
 I believe by default ubuntu uses acpi instead of apm so you should try the acpi equivalent of apm first. If you still want apm you can disable acpi by adding acpi=off to the kernel arguments.

---

### Post by blinksilver on 2005-03-09
[http://www.ubuntulinux.org/wiki/HoaryPM](http://www.ubuntulinux.org/wiki/HoaryPM) this is what  i will be trying,  in a little while

---

### Post by blinksilver on 2005-03-09
nada on both, will try with 2.6.11

---

### Post by Pse on 2005-03-09
I have not started to test that in my AMD64 box, but after I installed Hoary array 5, I had "hibernate" in the Log Out dialog enabled by default, so it should work. I'll certainly give it a try, as soon as I finish some other configuration tasks ](*,).
I was gonna go through that Wiki page you mentioned earlier to achieve other power states, so I guess it should work for you too.

---

### Post by kubla on 2005-03-10
[QUOTE=blinksilver]nada on both, will try with 2.6.11[/QUOTE]
 I got my laptop to hibernate today... it took a long time to go into hibernation mode and then I couldn't wake it up again :) Anyway, it's a start. I'll play around some more later... blinksilver that was with the 2.6.10 kernel, not 11.

---

### Post by blinksilver on 2005-03-10
cool, here is what i have experenced, i think you are right about the hibernate taking a  really long time, which make it pretty much useless, but if you want it to resume follow the instructions about adding the resume partition to your grub file in the guide marked above, you *should* get it to work, for me i get a weird IO error that can't seem to be fixed. as for the software suspend, followed the guide, added ndiswrapper to the list of modules to be removed and after hitting the sleep key, ndiswarpper get modprobe -r'ed, a few of the menu operations stop functioning and well thats it,  i have to hard shutdown after that, but i cam still move my mouse and call some progs.


for what its worth a friend of mine says that post 2.6.8 the the power mangement was  given a face life and beyond the speed imporvements, it also cause everything to break inside the power mangement, he could just be going overboard, but who knows

anyone else have some ideas, because i am fresh out

still have not tried 2.6.11, will do shorty, had cmps asg due

---

### Post by Pse on 2005-03-11
ACPI has always been a problem in Linux, but I think we're headed in the right direction. The only reason it was never really suported was because nobody really cared about doing a rewrite of the old code. Luckily, I think there are people already working on this, and as soon as we get good suspend and hibernate scripts/programs, we should get everything working properly.
BTW, I'd also heard about the ACPI layer getting a facelift...

---

### Post by blinksilver on 2005-03-11
any idea on a  time frame?????

---

### Post by ObjectWiz on 2005-03-11
I have hibernate working on my Acer Aspire 1524WLMi Athlon 64.  You just need to add:

resume=/your/swap_partition (which you can get from /etc/fstab)

to the vmlinuz line and then in the log out box, select hibernate.

Don't be fooled when it boots up to blackness... the screen is locked.  When the disk has settled down, wiggle the mouse and it should ask for your password.

Cheers,

Peter.

---

### Post by ObjectWiz on 2005-03-11
Actually, I guess you're meant to use the kopt setting for kernel options...

Peter.

---

### Post by blinksilver on 2005-03-13
i booted up to blackness, but even after 20 or so minutes i got nothing, the kernel just broke, even when i removed the command for grub, everything went to hell, sadly running windows now, until after my finals

---

### Post by kunjan1029 on 2005-03-17
anyone here got to get suspend to disk working with nvidia driver and not the nv?

on mine hp zv5260 i can suspend to disk and when i restart it will load everything up but then it will reboot as soon as i switch to  X display.. 

I vaguely remember reading somewhere that suspend to disk doesnt work on i386 because of the buggy nvidia driver

thanks!

---

### Post by blinksilver on 2005-03-18
don't own nvidia, sorry bud

---

