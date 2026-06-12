---
title: "Barely installable, generally unbootable"
date: 2007-02-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by mjancaitis on 2007-02-15
Hey, everybody - 

I've been poring over the x64 boards and some others trying to see if anybody else is having my problems, and I don't see anything. I previously was attempting to install Ubuntu to an external hard drive, as discussed in a thread about somebody successfully installing 5.10 to one; after that failed many times, I instead tried to merely install Ubuntu to my laptop's hard drive with a dual-boot, but install GRUB to my flash drive instead of Windows' MBR. Thought it would be fun to have some extra security, can't get into Linux without the flash drive. Whatever, thought I'd play around. Long story short, near as I can tell, I'm doing everything correctly, and having fun learning, but the whole shebangabang crashes or hangs damn near every time I try and boot it.

First, the LiveCDs can't boot - a regular Ubuntu LiveCD only works barely in safe graphics mode, hanging about half the time I try to boot into that; it hangs every time, without fail, in regular graphics mode. An Xubuntu LiveCD similarly will not boot. Hang city. I get hangs about 30% of the time using an Ubuntu Alternate Install disc as well, but the OS installs. When I try to boot into it, however, which I think I've done correctly after figuring out all my GRUB problems, it brings up a grayscale Ubuntu splash screen, tries to load, and fails miserably, just hanging there.

Specifics: the hardware is an HP Pavilion dv6140us, whose specs can be seen [here]("http://www.shopping.hp.com/store/product/product_detail/RG274UAR%2523ABA?jumpid=in_r329_search//dv6140us_RG274UAR"): dual-core 1.8 GHz Turion x64, 2 gigs of memory, 120 GB hard drive. The Ubuntu installs attempted have, I believe, all been version 6.10, fresh installs, so no upgrade problems, and I've used a 6.10 LiveCD, alternate install CD, and a Xubuntu 6.10 LiveCD. 

Sorry for the epic post, but I wanted to be thorough, and I'm getting incredibly frustrated. I haven't tried 6.06 yet, but I suppose if everybody thinks it might just be 6.10, I can try it. Anything you guys can offer me, I'll be grateful for. Thanks, everybody.

-Matt

---

### Post by hizaguchi on 2007-02-15
Have you tried booting without apic and acpi?  You can do that by hitting "e" when the Grub menu comes up and editing the "kernel" line of your Ubuntu installation so that you can add```
noapic acpi=off
``` at the end.

---

### Post by mjancaitis on 2007-02-15
Well, that worked to boot into a liveCD, which is more than I can say for other things. I'll try it with the install I currently have, and see if it works.

What does that code do that might explain my problem?

I'll post again after trying my installed version. Thanks.

---

### Post by wesley_of_course on 2007-02-18
Wesley here ;

 Haven't had this particular problem but was curious myself and found this ;
        [http://www.linuxquestions.org/questions/showthread.php?t=454675](http://www.linuxquestions.org/questions/showthread.php?t=454675)

  Hope it clears it up !?

---

### Post by mjancaitis on 2007-02-22
noapic and acpi=off works for the lappy. Even got my networking and graphics drivers working, too. Thanks, everybody.

---

