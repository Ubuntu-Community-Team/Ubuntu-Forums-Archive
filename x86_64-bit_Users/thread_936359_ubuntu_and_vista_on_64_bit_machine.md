---
title: "ubuntu and vista on 64 bit machine"
date: 2008-10-02
forum: x86 64-bit Users
---

### Post by nasrott on 2008-10-02
I have Ubuntu installed on a machine in a 320 gig sata drive, I also have a  1.2 TB raid 0 installation with Vista ultimate 64 bit on the same machine. I wasn't able to install the 2 in dual boot. My question is: Is there a way to manually add these 2 together now to make them dual bootable aside from picking the the drive to boot from in BIOS? Consider your answers as me being a newb to all this, with limited knowledge as far as linux goes.

Thx

Machine specs:

AMD QUAD 9850
1.2 TB RAID O  (Marvel raid)
320 GIG SATA
4 GIG 1066 RAM
2 x 3870's in crossfire
amd 790fx chipset based motherboard
razor baracuda sound card

thats about it,
rest really dosen't matter I don't think.

---

### Post by Sef on 2008-10-02
To make sure I understand what you want:

1) You have two hard drives: one with Ubuntu and one with Vista.

2a) Do you want put them on one drive?

2b) You are not getting a choice of which os to use and you want that.  

3) Which one is correct?

---

### Post by t4thfavor on 2008-10-03
Install windows, and leave some space for ubuntu either on the 320, or the raid volume. Boot the live cd, and install ubuntu to the extra space. When it asks to install grub, install it on the MBR. 

When you boot you will get the choice of wither Vista, or ubuntu, the latter being the default choice after 10 seconds.


You can modify the order of the choices by editing /boot/grub/menu.lst.

I think I understand the question, correct me if anything sounds funny.

---

### Post by nasrott on 2008-10-03
> **Sef said:**
> To make sure I understand what you want:

1) You have two hard drives: one with Ubuntu and one with Vista.

I have 3 drives in my system one is a raid0 which ubuntu will not install in and be visible after reboot other than looking at hte folder in windows I beleive this has to do with the raid0. The single sata drive not in raid is where ubuntu has installed it is the only space it sees when doing the install. 

2a) Do you want put them on one drive?

No that is not possible unless I moved the install of windows into the small sata, if possible would like to keep them where there are and get a normal boot screen with both as an option to boot into, like you mormally get with a dual boot

2b) You are not getting a choice of which os to use and you want that.


Exactly I don't get the option  and for the time being am using BIOS and selecting which drive order to set to see both of the Os's I have in now

3) Which one is correct?

2b)

---

### Post by nasrott on 2008-10-03
> **t4thfavor said:**
> Install windows, and leave some space for ubuntu either on the 320, or the raid volume. Boot the live cd, and install ubuntu to the extra space. When it asks to install grub, install it on the MBR. 

When you boot you will get the choice of wither Vista, or ubuntu, the latter being the default choice after 10 seconds.


You can modify the order of the choices by editing /boot/grub/menu.lst.

I think I understand the question, correct me if anything sounds funny.

Ya tried the normal method for example trying to install in a windows folder the thing cd errors out at 100% even tried the version 504 of the installer.exe and end up with no graphical, like xconfg is toasted some how.  

Have had ubnutu installed a few times over the years albeit on a system with no raid0 that windows was in at the start and the dual boot worked fine. 

Installing from cd on a windows folder in the sata or on the bare drive with no partition on the sata I end up where I am now with no boot loader from grub. Also cant even see windows folders now like I have always been able too on previous installs am assuming because windows is in a raid0.

Guess that Ubuntu cant see vista in my raid0 that this is my problem and was wondering if there is a app (boot loader) that could see both and would solve the problem I am in with out having to move vista out into the 320 gig sata. At least this is what I am hoping for...

---

### Post by Sef on 2008-10-03
Have you checked [Super GRUB Disk]("http://supergrubdisk.org")?

---

### Post by t4thfavor on 2008-10-03
Is the raid0 volume a hardware raid, or a software raid? if it is a software raid, then you will never see the windows data from inside linux. If it ais a hardware raid, does linux have the correct driver for the controller (stupid question),

Just some things to think about.

---

### Post by stmiller on 2008-10-04
Only way to dual boot a RAID setup is with hardware raid (which sucks- Linux software raid is much better).

Or have Windows on the RAID, then give a single partition on one of the discs for Linux.

RAID 0 is risky for an OS drive...

---

### Post by rplantz on 2008-10-04
I don't know how much this might apply, but I installed ubuntu on my Acer laptop with Vista. I'm a Windows newbie and do not have experience with RAID.

The problem I had is that Acer does not supply a Vista installation disk. They use a "hidden" partition on the disk to restore Vista if needed. When I installed grub it wrote over the Vista boot record, so I could not get to the hidden partition if I ever needed to restore Vista.

So I ended up using the howto at
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)
which shows how to use the Vista boot loader. Very easy to do, and it works quite well for me.

---

