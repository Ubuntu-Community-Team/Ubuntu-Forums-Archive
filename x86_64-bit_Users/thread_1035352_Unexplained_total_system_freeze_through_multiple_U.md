---
title: "Unexplained total system freeze through multiple Ubuntu mods"
date: 2009-01-09
forum: x86 64-bit Users
---

### Post by H0L7 on 2009-01-09
So far this has happened in Mint 6 x86, Ubuntu Ultimate x64, Ubuntu x64, Ubuntu x86. clean installs every time

all Ibex based

first off some basic info
kernel 2.6.27-9
Base 8.10 ibex
system lenovo thinkpad t61
Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz
3gigs system memory
GPU: quadro nvs 140m 512 vram
Sound Card:Intel corp 82801h ich8 family hd audio controler
Wifi: Intel Pro wireless 4965 a/g/n
hard  nic: intel 82566mm gigabit netowrk conection

now for the crash description 
I can not tell what triggers it but when everything freezes the wifi light and the caps lock light  begin blinking. sadly this seems to be the only information i can glean after crash.

please tell me anythin i can do to give whoever wishes to help me more info

---

### Post by MighMoS on 2009-01-09
I would install the kerneloops applet. (apt-get install kerneloops). To me it sounds like the kernel may be running into a bug on your configuration. If this happens again, when you reboot you should get a message telling you that your Kernel experienced a problem or something similar. And it will ask you to submit a report. Do so.

If that *doesn't* happen, then its not a kernel issue (or shouldn't be). Other things to check are /var/log/messages to see if anything 'suspicious' is in there.

---

### Post by H0L7 on 2009-01-11
thank you for your help I will submit a report after the next crash

I am actually quite worried about this as I have been using Ubuntu in one or another of its many forms as the os for may of my customers and i really did not want to go looking for another distro as this one is so easy for people to learn

most people are ecstatic when they hear they wont  be paying an extra 130 for an OS

---

### Post by Yellow Pasque on 2009-01-11
Since it happens across multiple distros, I suspect bad hardware (probably a RAM module). Press <Esc> when your system boots to access the GRUB menu. Select memtest86+ and let it run for a while (preferably while you're sleeping if you can hook the laptop up to AC power).

---

### Post by H0L7 on 2009-01-11
yea i didnt get a dump after the crash I am going to run memtest now

---

### Post by H0L7 on 2009-01-11
I ran memtest with no errors then i ran a 5 pass burn in with sandra under winxp still no errors. It was pleasantly surprising to see the processing power brought to bear by the t9300.

At this point I am once again of the opinion that this is os based and would be quite appreciative of further assistance.

---

### Post by gschwim on 2009-01-15
I have this same problem, but no blinking caps lock key.  It only seems to occur when I've been away from the computer for a short time.  I've tried a few theories out, including:

[LIST]
[*]Changing from a 3-D screen saver to simple the F-Spot slideshow
[*]Not running any KVM guest instances
[*]Disabling AMD Cool n Quiet in the bios, and removing all cpufreq* modules and related, plus disabling/killing powernowd.  This actually seemed to help a little, the system ran for 1.5 days instead of the usual half day.
[/LIST]

The platform is as follows:

[LIST]
[*] AMD Athlon X2 64 5050e CPU
[*] 4GB RAM
[*] 250GB EIDE HDD
[*] Onboard Nvidia 8200 video
[*] Motherboard is an Asus M3N78-VM
[*] Ubuntu 8.10 AMD64
[/LIST]

I had 22 VMs running under KVM on this system and it seemed rock solid for the several hours I had them running.  I walked away for 40 minutes, and came back to a totally locked up system, caps lock/num lock unresponsive.

Interestingly, I have a Dell Opticrap something or other at work, also 4GB RAM, but with an Intel Core 2 Duo (no VM extensions), and an ATI X600 (I think) video card, and it does the same thing, albeit maybe 2x a week and not every day.  That system is running 8.04 32 bit.

Tonight, I'm going to kill GDM, load all 22 VM guests, and let it run all night.  Maybe its the video driver.  If that fails, its a memtest, and assuming that comes out OK, its on to trying some other distribution, or (please don't make me do this), V1$t@. :(

---

### Post by j.diddy on 2009-03-04
I'm getting the same symptoms-- total system freeze (but no caps lock blink or any other activity; doesn't even respond to ping) at irregular intervals, sometimes twice in one hour, sometimes not for a week.

generic system: Intel DP43TF motherboard with Core2 Duo E8500 at 3.16GHz, nVidia XFX GeForce 8500 GT video board, etc.
OS: Ubuntu Intrepid 8.10 (kernel 2.6.27-11)

Any advice on tracking down and fixing the problem would be greatly appreciated. I have system administration experience but not recent, and almost zero with Ubuntu.

---

### Post by marcelkoopman on 2009-03-04
Here's something that might help.
I've disabled IOMMU. This made my system more stable.

You can add to your grub configuration the option "iommu=false" for the kernel you are using.

---

### Post by dakaujunk on 2009-04-28
I too have the same problem. After a while of using my system, the system freezes with the caps lock blinking. There does not seem to be any pattern or any event triggering this freeze. I also tried to boot window$ xp sp3 to see if this problem occurs there. Surprisingly M$ window$ seem to work fine. But I hate to work in window$. 

I am going to try the 2 solutions (iommu & kerneloops) posted in this thread to see if that helps.

Can someone help me in this?

System details:
Thinkpad T61
Intel Centrino Pro T7500 2.2 GHz
3 GB of RAM
100 GB 7200 RPM Hitachi hard disk
Hitachi 8x DVD burner
NVidia Quadro 140 128 MB VRAM

OS details:
Linux Mint 6 32 bit
Linux ****** 2.6.27-7-generic #1 SMP

---

### Post by dakaujunk on 2009-05-03
I've tried iommu=false (suggested by someone on top of this page) and kerneloops in vain. Kerneloops does not even seem to know that the kernel has hung before.

I still have this issue. Anyone still experiencing this unexplained freeze issue?

---

### Post by aLmastro on 2009-05-03
gschwim I'm having the same problem as you and I'm using the same Asus board. Before I installed that board I had never had the problem.

---

### Post by j.diddy on 2009-05-04
About 3 weeks ago I loaded the then-latest nvidia driver (was 177; I'm now running with 180.11), and am happy to report not a single freeze since then. If you haven't updated your video driver recently give that a try.

---

### Post by dakaujunk on 2009-05-19
My 2 cents:

As per the response from a Linux Mint Xchat user, upgraded to the latest kernel. That has solved my problems of system freeze. Now happily running my laptop continuously for the past 2 weeks with no issues.

---

