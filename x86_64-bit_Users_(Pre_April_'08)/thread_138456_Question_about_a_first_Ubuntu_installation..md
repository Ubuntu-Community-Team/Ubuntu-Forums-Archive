---
title: "Question about a first Ubuntu installation."
date: 2006-03-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Hoffmann on 2006-03-01
Hello All:

This is my first posting on this forum.
A couple of days ago, I ordered my Ubuntu CD. Since my architecture is the EM64T, that installation CD is the 64-bit PC (AMD64) one.
Ok. At the moment, I have a Windows XP/Linux dual partition, as shown below:

/dev/sda1     fat32                             9.50GB      HP_RECOVERY
/dev/sda2     ntfs                             59.59GB      Windows XP
/dev/sda-1    free  (status: hidden)      4.62MB
/dev/sda3     ext3                           161.60GB      Linux
/dev/sda4     extended                        3.18GB
/dev/sda5     linux-swap                      3.17GB
/dev/sda-1    free  (status: hidden)       7.84MB

The computer bus technology on my machine is SATA, and the (dual) boot program is GRUB. Moreover, I have an external HD (formated as fat32). My idea is to install Ubuntu where my current linux partition lives, in order to have a Windows XP/Ubuntu dual boot.  
QUESTIONS:
(1) Is that possible? I mean, during the installation process can I remove my current linux distro; install Ubuntu where that distro lives (if possible remove those unecessary free spaces); and keep my windows partition also working?
(2) Does Ubuntu recognize SATA?
(3) What about GRUB? Is a new GRUB installation going to be done? Any conflict there?
(4) Is my external HD going to work on both my Windows and linux partitions, as it is (nicely)  working now?

In case that procedure  (1 - 4) being complicated, could you guys, please, send me any hint?

Many thanks in advance!
Hoffmann:)

---

### Post by Strangerdave on 2006-03-01
[QUOTE=Hoffmann]Hello All:

This is my first posting on this forum.
A couple of days ago, I ordered my Ubuntu CD. Since my architecture is the EM64T, that installation CD is the 64-bit PC (AMD64) one.
Ok. At the moment, I have a Windows XP/Linux dual partition, as shown below:

/dev/sda1     fat32                             9.50GB      HP_RECOVERY
/dev/sda2     ntfs                             59.59GB      Windows XP
/dev/sda-1    free  (status: hidden)      4.62MB
/dev/sda3     ext3                           161.60GB      Linux
/dev/sda4     extended                        3.18GB
/dev/sda5     linux-swap                      3.17GB
/dev/sda-1    free  (status: hidden)       7.84MB

The computer bus technology on my machine is SATA, and the (dual) boot program is GRUB. Moreover, I have an external HD (formated as fat32). My idea is to install Ubuntu where my current linux partition lives, in order to have a Windows XP/Ubuntu dual boot.  
QUESTIONS:
(1) Is that possible? I mean, during the installation process can I remove my current linux distro; install Ubuntu where that distro lives (if possible remove those unecessary free spaces); and keep my windows partition also working?
(2) Does Ubuntu recognize SATA?
(3) What about GRUB? Is a new GRUB installation going to be done? Any conflict there?
(4) Is my external HD going to work on both my Windows and linux partitions, as it is (nicely)  working now?

In case that procedure  (1 - 4) being complicated, could you guys, please, send me any hint?

Many thanks in advance!
Hoffmann:)[/QUOTE]


1a) from what I can see, the installation should work.
1b) from my experience you install Ubuntu where you want it and it will delete what is there, format what is there, and install Ubuntu.
2) I am pretty sure Ubuntu recognizes SATA, but I would suggest that you search the forums.  From what I saw, there should be no problems.
3) Grub will most likely be installed and if you put in the master boot record, you should be able to dual boot.  It will give you the oppertunity to boot to either OS.
4) That last question is a bit beyond my expertise.  I would wait to see what other think.

Hope that helps.

-SD-

---

### Post by seannyob on 2006-03-03
[QUOTE=Hoffmann]
/dev/sda1     fat32                             9.50GB      HP_RECOVERY
/dev/sda2     ntfs                             59.59GB      Windows XP
/dev/sda-1    free  (status: hidden)      4.62MB
/dev/sda3     ext3                           161.60GB      Linux
/dev/sda4     extended                        3.18GB
/dev/sda5     linux-swap                      3.17GB
/dev/sda-1    free  (status: hidden)       7.84MB
[/QUOTE]

That's *waaaay* too much swap space.  All you need is about half your RAM, maybe about 512 megs at most.

Also, I just installed last night and my SATA was recognized and the Ubuntu installer modprobe'd sata_nv, which is the F/OSS nvidia sata driver, YMMV depeding on your hardware, but it'll likely detect.  (This was 5.10 Breezy)

Consider a root partition, a home partition, then a /media partition for songs and music, that way if you want to switch distributions later you can blow away the root partition and not have to worry about losing your personal data.

---

### Post by Hoffmann on 2006-03-03
seannyob:

I am glad to know that all is working great with your installation. I am anxious to receive my Ubuntu (5.10 Breezy)  CD. Could you (or another person), please, give me more details about a good partition plan? I did like your information about not loosing personal data after installing a new distro. I didn't understand how is it possible to switch distributions without loosing personal data. I mean, /home partion will be working for a new distro???
Regarding memory RAM, I have 1GB, and I intend to increase it to 2 or 4 GB in the future. In this scenario, could I also hear from you gruys about a more 'rational' swap partition size?

Thanks!
Hoffmann

---

### Post by seannyob on 2006-03-03
Hoff,

512 megs of swap is all you need.  If that.

If you reinstalled you could map your new home to the old /home partition, sure, but it'd be alot of work mapping the new users to the old UIDs, some people think it's not worth it, some do.  Do it with home or make up something like /media or /file or something stupid like that, either way keep your data on a separate partition that is independent of your distribution, so you that you can just reinstall if you feel like it without having to back your stuff up from another drive or discs. There are other benefits to putting things on different partitions, mainly that those partitions won't fill up if an application starts writing to disk like mad.

There's tons of data on partitioning effectively, security, etc out there on google.  Found this with a really quick search:
[http://linuxhelp.blogspot.com/2006/01/effective-partitioning-how-and-why-of.html](http://linuxhelp.blogspot.com/2006/01/effective-partitioning-how-and-why-of.html)

What do you need 4 megs of RAM for?!?!?! Are you rendering special effects for ILM or something?  Can you get me Lucas' autograph!?!?  ;)

---

### Post by Hoffmann on 2006-03-03
Hello seannyob,

Many thanks for the information and for the website. I will take a look on that website and, if necessary, I'll be back to the forum. The reason for so much memory is that I also use my machine for working. That is related to molecular simulations and modeling. But, probably, instead of 4 GB of RAM, 2 GB would be enough. Even as my machine is right now (1 GB RAM) it is good for my simulations.

Best,
Hoffmann

---

