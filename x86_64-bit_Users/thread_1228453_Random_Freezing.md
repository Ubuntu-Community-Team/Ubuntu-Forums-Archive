---
title: "Random Freezing"
date: 2009-07-31
forum: x86 64-bit Users
---

### Post by faiakeima on 2009-07-31
I recently installed Ubuntu 9.04 64-bit on my computer in a dual boot with XP Pro. Every so often it would freeze up. So, I installed Kubuntu 9.04 64-bit instead to see if that would help solve my issues. Unfortunately it didn't help any. Usually this will happen what seems randomly, and the way it freezes is in that I can not move the mouse or type anything, and I have to manually turn off my computer. When I run XP this never happens. I'm still new to Linux so I don't know how else to explain this. Some of the specs on my computer are:

AMD Athlon 64X2 2.9ghz Processor
5gb of RAM
ATI HD 2400 512mb PCI-E Graphics Card

Thank you for any help.

P.S. I realized that this never happens on my laptop, which has lesser specs. The main difference is that my laptop is an intel x86.

---

### Post by JohnLau on 2009-08-01
):P faiakeima, I think we need more details, like whether you have installed the proprietary driver, or what applications you were running when it freeze(firefox / flash player)?

Also, when your computer freezes it's better to press alt + prtscr + REISUB (press REISUB one by one while holding alt and prtscr) to reboot your machine because it reduces the chance of losing data...

John

---

### Post by musther on 2009-08-02
I've been having the same issue:

Intel Core 2 Quad
9.04 64 bit

Very hard to track down - I've done extensive memory testing, seems fine, nothing in the logs.  I read something somewhere which suggested a wireless issue, so I'm trying to not use it for a while, see if it helps.  Are you using wireless?

---

### Post by wfp on 2009-08-03
I was having a lot of random freezing what worked for me was using cpu frequency scaling monitor, and set my cpu to a higher Ghz. I use desktop effects, and awn, and screenlets. With cpu set to on-demand I would get constant freezes. I have not had a freeze in about six months now. On demand just does not work good on my box for some reason.

---

### Post by musther on 2009-08-03
What scaling monitor/controller do you use?

---

### Post by wfp on 2009-08-03
Right click your panel> add to panel choose cpu frequency scaling monitor.

---

### Post by fredfox on 2009-09-08
I have had a similar experience, but with some twists:

I ran Jaunty (always up to date) until the end of July with no problems on a HP pavilion AMD Athlon X2 4200+ with 3GB ram. The machine was off for one month and dead when a restart was attempted. I moved the disk to another machine, Gigabyte MB with AMD Athlon X2 4200+ and 1GB ram. Did updates and installed Nvidia proprietary (this machine has Geforce 7300GT) and began experiencing "Random" freezes. I connected to this machine via ssh and the freezes were complete, with even the ssh session being dead. No log messages were ever generated at the time of the freeze. Removing the Nvidia proprietary drivers did not help.

I noticed that with every freeze, the CPU Frequency Scaling Monitor on the panel showed both CPUs at maximum frequency, and that the freeze occurred after the frequency had dropped to minimum frequency once or twice. I also noticed that I could get the freeze to occur by loading the machine to get the CPU frequency to increase.

I disabled AMD cool and quiet in the bios and the machine has not had a freeze for the past 20 hours.

The mystery is why the old machine did not have any problems while this one does. I ran the proprietary drivers on the old machine (Nvidia 6160 integrated with dedicated ram). When moving the drive, the proprietary driver needed to be disabled before it would go into X properly. Could there be problems with a buggy bios?

Should I submit this as a bug, and what info should I include.

---

### Post by ronparent on 2009-09-09
I initially unsuccessfuly tried 9.04 live cd on three computers with amd64 cores. I eventually got to run on all of them on the live cd by using F6 at the first screen after language selection to deselect apic and lapic. I installed with noapic,nolapic kernal loading option and virtually eliminated the freezes.

That said, there seem to be more than on causes for freeze. On this machine I'll get a freeze if I try to use a trackball mounted in tandom with a mouse. The doctor says 'don't do that any more' - so I don't.

---

### Post by Michael Knap on 2009-09-09
I have been tracking down some similar problems on my desktop. I have narrowed it down to perhaps some schedule-clock issues. You may want to take a look at some older logs after you reboot, you may find something referencing clock-src. There are some boot parameters you can use, too, that will offer you a few options to test different clock-srcs. There is more information available, but I don't have access to it right now.

---

### Post by Tarcisu on 2009-09-09
I have been running Jaunty-64 on my laptop since I got it and have also been plagued by this problem, but I believe I have corrected it.

Specs:  Lenovo Y550
Intel core 2 duo 2.53ghz
Nvidia graphics

In BIOS, I changed the hard drive mode from AHCI to IDE.  Since then, I have not had any of these random freezes (has been over 30 hours, used to freeze at least once every 3-4 hours).

Hope this helps.

---

### Post by foo1797 on 2009-09-17
I'm also getting random freezes with my Wife's computer. 

 Athlon 64 dual core, pci-e nvidia 7200 graphics, atheros wireless driver... as the machine's frozen right now, I can't update with more info 

 I note that a previous use also had an nvidia graphics chip.  This happens to my wife most often while using firefox, and this has happened to me remotely doing apt-get update or in the middle of long-ish rsync, so I'm becoming suspicious of the wireless card. 

 I don't remember setting up any of the amd power saving stuff, but when I get home I'll attempt to disable in the bios and see if that helps.

---

### Post by bodam on 2009-09-18
I too am seeing these random freezes.  95% of the time it occurs when I'm away.  I come back and the box is completely frozen - not even the mouse moves.  I have to hard boot.  It's hard for me to say what application it is because I tend to leave quite a few open (e.g. Firefox, Evolution, songbird, Pidgin & Transmission amongst others.

That being said, i have had it freeze on me when I have used it too. I am looking for suggestions too.  I am a novice user so go easy on me.  

I checked my performance scaling and I have it set to on demand too.  I see some suggestions to change it.  Any suggestions on a test setting?

---

### Post by foo1797 on 2009-09-18
I turned off cool n quiet in the bios last night and had freezes. 

I'm leaning towards this being related to the wireless network card, because booting up the machine and leaving it alone gives an uptime in hours (however I've got smokeping polling the machine, so it's not going to be entirely free of the network), but if I start an rsync over the local network she'll freeze in under 10 seconds. 

my network card is an Atheros AR5001X+ and both ath_pci and ath5k cause lockups just as quickly. 

Currently I booted the machine under RIP linux and am running a backup of my wife's homedirectory, over the net and I've not only passed the 10 second mark, I'm over the 1 hour mark, so this doesn't look to be hardware related.  Last night I ran a full cycle of memtest86+ and had no errors. 

Under ubuntu 8.10 the machine was solid, and problems only started with the upgrade to 9.04, so it seems to be related to the particular kernel/network module combination.  this is 2.6.28-15

---

### Post by foo1797 on 2009-09-21
I tried booting with &quot;noapic acpi=off&quot; and still had freezes quickly after a decent amount of network traffic. 

Booting with nosmp solved the issue.  However the nvidia module apparently wouldn't work with smp off, so in the end to get everything working I had to recompile my kernel and modules after configuring no smp. 

So this looks to be a temporary workaround and I'll hope that the kernel that comes with ubuntu 9.10 works without lockups.

---

### Post by foo1797 on 2009-10-19
So, replying to myself again; turning off smp didn't actually make things stable; it just pushed uptime into the realm of 3-4 days .  Then 1 day.  Then hours, and finally the machine wouldn't get to post.  It turns out either the CPU or motherboard died.  Wanting to get the machine up and stable immediately, I bought a new mobo and cpu and the nvidia card and atheros wireless card are working perfectly with the new hardware.

---

### Post by D-Sider on 2009-10-19
I have a similar issue, but I'm not using Wireless.

Pentium Dual Core 2.5Ghz
4GB Ram
ATI Graphics without the prop driver
Intel chipset based motherboard
ReiserFS formatted drives +2 NTFS storage drives used for dual boot.

I only noticed the issue after installing and updating Jaunty.  I updating almost immediately after installing.  So, I tried using the older (-11) kernel.  At first this looked to have corrected the issue because the computer was fine for about 4 hours (as opposed to 30 minutes max). But then the same thing happened. Sam problem as everyone else in all the other threads describe.

It seems to primarily affect 64-bit users.  But there doesn't seem to be a clear-cut solution. A few people have said updating to 9.10 Beta (or full version in a week) seems to fix the issue. But it's pretty frustrating in the mean time.

---

### Post by lynnejohn on 2009-10-20
I have similar problems except my system can't run for more than a few minutes after install. Mouse still moves, but keyboard and everything else are non responsive. My system setup:

Gigabyte GA-EP45-DQ6
NVIDIA GeForce 9800 GT
Intel Core 2 Quad  Q9550
8Gb DDR2 1066 Performace

Other notes from my testing:
None of the install options seem to make a difference (F6).
Suse 11.1 also exhibits the same problem.
FC11 does not have an issue.
I have only tried 64bit installations.
Memory testing for 24 hours runs clean.

I would prefer to use Ubuntu but I need to get somewhere with this. I'd like to seperate wether it is a video card issue or not. Is there a way during install that I could force it to use a generic driver? Or possibly a way to dump out the differences between the FC11 and Ubuntu settings for CPU/system?

Thanks,
    John C.

---

### Post by Pandorange on 2009-10-24
Similar problems here too.
It happened on a AMD_64 NVidia Desktop computer and keeps happening on an AMD64 NVidia Laptop.
Nothing seems to trigger the freezes.
On the Laptop it was problematic for getting the upgrades and security updates. It even freezes in tty1 when trying to get the upgrades.
At the moment the best solution for me, is to go back to Hardy.
Before going back to Hardy, is there any information I could harvest that would be of interest to the team of developers?
I noticed that we are not alone in having these problems ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/347848](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/347848))

---

### Post by Arnem on 2009-11-03
My Desktop also randomly 'freezes'. Well, actually it doesn't freeze completely but all the USB-devices stop working. (Keybord, Wifi-adapter, mouse). 

Now I think it's because I added a rule to the /etc/fstab configuration-file to make the USB devices work in Virtualbox. Something goos wrong with that rule I guess. Did the people which have similar problems also add that line to the fstab file?

---

