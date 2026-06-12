---
title: "Ubuntu Freezing / V. Unstable"
date: 2005-06-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by speedsix on 2005-06-14
Hi,

New user to Ubuntu, fairly new to Linux in general. Having lots of problems getting Ubuntu running stable.

It installls fine but will hard lockup after a random period of time, I cannot move the mouse, use the keyboard or even login via SSH. The only solution is to reboot the system. I can replicate this every time by repeatedly resizing a window or table column, it will always lockup doing this.

I have searched the forums and found several posts with very similar issues, one post suggested adding the line 'NOAPIC' to the grub menu.lst file for my kernel. This actually stops the hard lockups completely but instead renders the system very unstable, programs crash, high cpu useage, laggy  mouse, lots of error messages and my gnome seems to get completely corrupted. Also tried acpi=offf.

Following is some more information about my system and everything else I  have tried;

AMD64 3000+
1Gb ram
Gigabyte nForce3 mobo
Sata HD, IDE dvd writer
ATI Radeon
usb mouse

Ubuntu 5.04 64bit (also tried 32bit same issues)
Suse 9.2 works fine
Live cd's (Kubuntu) seem to work fine (HD access issue maybe?)
Tried a full install of Kubuntu and it still locks up but much less than Ubuntu

1. Tried updating kernel from Ubuntu Update, installed all other available updates
2. Tried K8 kernel
3. Tried disabling powernowd as suggested in another thread
4. Tried updating bios / setting to failsafe defaults / disable usb2.0
5. Tried recovery mode
6. Tried updating nforce drivers
7. Tried 'vesa' video driver in place of 'ati' driver
8. Tried non usb mouse 
9. Commented out 'load dri' in X config
10. Added 'RenderAccel false' in X config


Any help would be greatly appreciated

Dom.

---

### Post by desdinova on 2005-06-14
One thought - try disabling acpi?

---

### Post by speedsix on 2005-06-14
[QUOTE=desdinova]One thought - try disabling acpi?[/QUOTE]

Tried that aswell,

thanks

Dom

---

### Post by skylark on 2005-06-14
This is a bit of a long shot considering you had no problems with Suse, but I think it is worth trying anyway. Download and run the memory checking program from [http://www.memtest.org/](http://www.memtest.org/) for about 3 or 4 hours to see if it picks up anything. Possibly you could have some hardware problem that developed recently... this might find it.You could also test the hard drive with fsck. Something like fsck /dev/hda ?

As a last resort u could do a re-install, and during the install check the integrity of the CD (there is an option in the install menu from memory).

---

### Post by speedsix on 2005-06-14
Hi, the same machine also runs XP without a problem so the hardware is ok.

I will try and verify the cd but I also tried the Kubuntu install and that had problems also. It seems the new kernel used in Ubuntu as opposed to the slightly older version in Suse 9.2 has issues with my hardware.

Is anyone else running Ubuntu on amd64 with an nForce3 board successfully?

Clutching at straws a bit now, if you search the forums for 'amd64 freeze' it returns quite a few posts with what looks like the exact same problem but no real solutions :(


Thanks alot

Dom.

---

### Post by speedsix on 2005-06-15
Hi, just to clarify it now seems to be 2 separate problems.

1. Hard lockups of the kernel requiring a reboot, cannot SSH in.
2. X crashing, laggy mouse, high Xorg cpu usage, programs crashing, SSH possible

I have been changing various things all morning and have actually, touch wood, seemed to have cured both issues but am a bit confused as to which cured which problem.

I'm pretty sure the **powernowd** is causing problem 2. X to crash and go laggy, I ran the machine for at least 45mins opening about 50 programs!! As soon as I launched powernowd which had been killed on boot, the problems returned instantly, lots of errors and v laggy, needed a reboot.

I'm not 100% sure what fixed the hard kernel lockups which was the initial problem, I thought it was adding the 'noapic' line to the grub menu but I have removed this now with no reoccurrence. I have a feeling it may actually be the acpi=off option afterall.

Will keep this thread updated.

---

### Post by speedsix on 2005-06-15
Right I've sussed both problems (well 99% sure ;))

1. Kernel Lockups
Change display device driver in /etc/X11/xorg.conf from 'ati' to 'vesa'

2. X crashing
chmod a-x powernowd


I may try and get an updated ati driver but I don't use 3d so it's not really a problem, card is Radeon 7000 btw.


Dom

---

### Post by NickB on 2005-06-15
I've resolved kernel lockups using the ati driver by setting Option NoAccel yes in /etc/X11/xorg.conf.  YMMV

Nick

---

### Post by gonenowhere on 2005-06-16
I also had this problem just installe ubuntu today i have 1 gb of ram and i dont think it  likes that. so if you have this problem take out a stick of ram and see if it works.

---

### Post by speedsix on 2005-06-17
[QUOTE=NickB]I've resolved kernel lockups using the ati driver by setting Option NoAccel yes in /etc/X11/xorg.conf.  YMMV

Nick[/QUOTE]

Hi yes this does work but is very slow.

Do you know of anymore solutions apart from using vesa or setting noaccel?

Many thanks

Dom

---

### Post by jyp on 2006-06-13
Hi

Sorry for the delay; I switched to Kubuntu so I don't read Ubuntu forums often.

Anyhow, up to now, very pleased with Kubuntu ; I did a fresh install using the alternate cd because I find the text installer more flexible especially for setting up partitions. I used the expert noapic nolapic options and now it seems to be solid. I experiences some freezes before but installing the nvidia drivers has cured the problem; I even now have the 1920x1200 screen resolution that I could not get in Breezy. 

But I cannot get skim working for Chinese input!

---

### Post by kizmat on 2006-07-13
I have the freezing problem as well, aparrently it was after I installed the linux-dri-modules. Everytime I started gedit, or when it is running scrensaver for a while, the system will freeze. Installed dapper on a T41 (radeon mobility 7500). 

Finally solved the problem by commenting out /etc/X11/xorg.conf  # Load DRI

Hope it helps.

---

