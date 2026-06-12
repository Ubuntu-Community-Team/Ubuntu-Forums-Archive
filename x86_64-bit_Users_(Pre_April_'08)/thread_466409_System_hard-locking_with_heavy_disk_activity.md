---
title: "System hard-locking with heavy disk activity"
date: 2007-06-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by cmost on 2007-06-06
Ever since I upgraded from Edgy to Feisty, my computer periodically hard locks.  I have to press the reset button to reboot.  I first noticed it when running VMware Workstation (which is fairly disk intensive.)  I've verified the correlation by being able to successfully hard-lock the computer when running the /etc/cron.daily/prelink script which is very disk intensive the first time run.  I would like for my computer to not lock up.  I'm doubtful I have a hardware issue as my system is fairly new and performed flawlessly under Edgy and Dapper before it.  I wonder if it might have something to do with the fact that a clean Feisty install will use the SCSI disk drivers for IDE drives (changing hda to sda, etc.).  Since I did an upgrade from Edgy, my drives have retained their hda designations.  Or, perhaps Feisty's version of the kernel 2.6.20 isn't happy with my hardware for some reason.  Perhaps I need to compile a custom kernel (assuming the computer won't lock up during the compilation!)  Can anyone offer me any insight into this annoying problem or offer suggestions other than a wipe and fresh install?  If I wipe my hard disk, I'll likely hop to another distro.  Ubuntu is beginning to annoy me and my last few posts to these forums have resulted in no replies.  Thanks.

---

### Post by stokkes on 2007-06-06
I don't have a solution for you, but if you do find something, could you please let me know?

My thread: [http://ubuntuforums.org/showthread.php?t=466374]("http://ubuntuforums.org/showthread.php?t=466374")

I've noticed that when my system does hardlock, I'm doing some disk activity. Unfortunately, I can't recreate it since I don't have /etc/cron.daily/prelink (not sure why).

I'd really like to get to the bottom of this.

---

### Post by cmost on 2007-06-06
Hi, thanks for the quick reply!  I reviewed your thread.  I see no one has posted any insight or suggestions for you...typical.  Ask a question about how to get some Windows game working in WINE and you'll receive fifty replies; ask a more difficult question and the community stands mute.  Oh well, I digress.  Can I ask whether or not you did a clean installation or an upgrade from a previous version?  Also, can you parse your server logs to see if you can determine if a significant amount of disk activity preceded the lockup?  For example, if you can nail down an approximate time that the machine locks and then look at time/date stamps on activity logs right before the lockup.  I'll try to do the same but I don't store logs on my workstation for very long.  Finally, what is your hardware configuration?  Mine is in my profile signature.  Maybe we have some common hardware that Ubuntu doesn't like.  Thanks.  Meanwhile, I'll keep researching the problem and see what I can come up with.

---

### Post by stokkes on 2007-06-06
I'm looking at syslog, kern.log and a few others, there's nothing in them.

I just had my system hard lock doing a "du -h ." in a directory on a hard drive and the system locked hard. I was doing this via SSH and tried to get to my machine, but the screen was blank when attempting to use the machine directly.

it's really bugging me.

---

### Post by darknightuk on 2007-06-06
what hard drive do you have?
have you run any diagnostic programs?
could be poss that ur drive is developing or has developed an intermittent  mechanical fault that is only showing when u push the drive/s, are you hearing any noise that stands out clunks grinding etc?

---

### Post by stokkes on 2007-06-06
I have three drives:

40GB Seagate boot/root
250GB Maxtor storage
500GB maxtor storage

SMART returns everything's "O.K."

no odd noises.

My System Specs:
AMD Opteron 170
Asus A8N-E
2GB of ram
(Those hard drives above)
BenQ DVD burner
nvidia geforce 7800gt using the nvidia driver (although it's a server, gdm does load up, but i don't login unless i need to use it for something quick).

Pretty much it.

---

### Post by cmost on 2007-06-06
I see we have ASUS motherboards in common as well as Nvidia graphics.  I know that my ASUS motherboard has some odd quirks that, for example, prevent AGP from functioning when a 32 bit OS is used.

---

### Post by Cappy on 2007-06-07
Feisty has a freezing problem and there is a big long thread on it. [http://ubuntuforums.org/showthread.php?t=405605](http://ubuntuforums.org/showthread.php?t=405605)
You should try adding "noapic acpi=off" onto the end of your /boot/grub/menu.lst line that you use to boot. That fixes it for most users.

---

### Post by cmost on 2007-06-07
Thanks cappy!  Will try that later this evening.  I don't know how I missed that thread, I did a fairly extensive search on the problem.  I'm also going to attempt to compile a custom 2.6.21.3 kernel package for Feisty amd64 and see if that helps any.

---

### Post by stokkes on 2007-06-07
cmost, what kernel are you currently running?

I know I installed uBuntu 7.04 Server for AMD64, but for some reason, my kernel returns generic.

---

### Post by cmost on 2007-06-07
The generic kernel is all there is right now.  Ubuntu consolidated the myriad of kernels in favor of a single generic kernel.  I'm currently running the recently updated 2.6.20 kernel.  I'm going to compile a custom 2.6.21.3 from kernel.org later this evening.

---

### Post by rplantz on 2007-06-07
> **Cappy said:**
> Feisty has a freezing problem and there is a big long thread on it. [http://ubuntuforums.org/showthread.php?t=405605](http://ubuntuforums.org/showthread.php?t=405605)
You should try adding "noapic acpi=off" onto the end of your /boot/grub/menu.lst line that you use to boot. That fixes it for most users.

There's an even longer thread, [http://ubuntuforums.org/showthread.php?t=412125](http://ubuntuforums.org/showthread.php?t=412125). I suppose one test of your system is seeing if it will stay up long enough to read the entire thread. :) In my post (#307) in that thread I describe just how weird my system is behaving.

I seem to have pretty good luck with my system if I don't try to enable beryl or compiz. I have removed the suggested kernel options (in menu.lst) and am avoiding beryl/compiz. My system has been stable for several days now.

Meanwhile, I've installed FreeBSD on another disk.

---

### Post by cmost on 2007-06-07
I've been running Beryl/Compiz since their very early days, without incident.  If Feisty all of a sudden has a problem with compositing then they need to fix it pronto.  I'm not willing to give up Beryl, or any other feature, to avoid locking my system.  The devs need to figure out why this is happening and issue a patch.  I'll try switching kernels, turning off ACPI or simply hop to another distro.  Thanks for your input.

---

### Post by cmost on 2007-06-16
Does anyone have any suggestions on this problem yet?  I tried the "add noacpi...." to my menu.list file but that hasn't solved the problem.  I hope the community can offer some remedy before I end up leaving Ubuntu for another distro.  I can't tolerate system lockups.

---

