---
title: "&quot;noapic&quot; has anything to do with laptop heat dissipation?"
date: 2008-03-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by sethu_iiit on 2008-03-31
Hi,
I am a Linux newbie and find it great to work on Ubuntu these days in my laptop.I have installed Ubuntu 7.10 Gutsy Gibbon 64-bit version. But I have this problem of laptop dissipating much heat when I work on Ubuntu than compared to working on Windows Vista. 

My laptop configurations ;
Model - HP Pavillion dv6449us
Processor - AMD Turion 64*2 mobile technology, 1.8 GHz
HDD - 160GB SATA disk
RAM - 2GB RAM

I use 'noapic irqpoll noirqdebug' as my boot options to install Ubuntu successfully it?on my laptop.

My question is, why this over heating problem occurs while working on Ubuntu and does this kernel parameter of 'noapic' has anything to do with it?

PS1 : My CPU idle percentage is around 99%, when i don't run any process
PS2 : It has not hanged or freezed  so far, thankfully :)

Thanks for your replies in advance...

Cheers,
Sethu

---

### Post by majnun on 2008-03-31
hi,

have you updated your system after install? sometimes this fixes things that don't work just installed

otherwise, on a shell type a 'top' command, sort by CPU (pressing shift+p)   and post which process is causing this 99% of CPU 

I'm on a presario v6000 (v6640es turion x2, like yours) and hardy heron works fine :-) well the wifi has issues but the rest is ok.

ACPI (not APIC) manages fan and power management, why did you installed with so many IRQ options?

---

### Post by sethu_iiit on 2008-03-31
Hi,
I have just updated my system with all the important security updates.

You have misunderstood that i get 99% cpu usage..But I have mentioned Its 99% IDLE when I am not running any process(So, that's normal).

These IRQ options are used at various places in the forum to install properly without any boot up problems.I will tell you, I had my tougher days trying out all possible Live and Alternate CDs of Ubuntu and have finally settled with this options working well with the 64-bit version live cd..

Is there any way I can reduce the heat that is generated excessively on ubuntu?

Thanks Again!

Cheers,
Sethu

---

### Post by m.hricko on 2008-04-01
Hello,

I have the same problem. But I mentioned, that the computer temperature is normal in 32bit system, but in 64bit is rising very fast. I posted a question on this forum [http://ubuntuforums.org/showthread.php?t=737601]("http://ubuntuforums.org/showthread.php?t=737601")   but until now I havent found solution.

milo

---

### Post by o.besner on 2008-04-01
I have the same problem with my laptop (HP dv9417ca) and I use the same line (noapic etc.) There is no easy way to fix it, sadly.

But I have great news. The issue is fixed with Hardy Heron and the new kernel. So in three weeks your computer will be running very smoothly. Until then...

---

### Post by alejandro.mc on 2008-04-02
Oh that's great news! Because I have the exact same problem in my F506LA..

Hope Heron brings more great news! =)

Good luck to everyone!

---

