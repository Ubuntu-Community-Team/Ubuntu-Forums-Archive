---
title: "Please Help: Ubuntu not recognising SATA"
date: 2006-07-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Pamir on 2006-07-26
Hello experts,

I am trying to install Ubuntu on HP Proliant ML 150 Sever with Adaptect SATA (Serial ATA - plug-in card - PCI-X hot-plug 66 MHz) I tried 2 different CDs. 

When tried with Ubuntu 5.10 64-bit, can not go beyond partintioning.On the partintioning page there is three option and none of the works.

When tried with 6.06 64-bit it hans with a blue screen

Can some one help me please?

---

### Post by Kilz on 2006-07-26
> **Pamir said:**
> Hello experts,

I am trying to install Ubuntu on HP Proliant ML 150 Sever with Adaptect SATA (Serial ATA - plug-in card - PCI-X hot-plug 66 MHz) I tried 2 different CDs. 

When tried with Ubuntu 5.10 64-bit, can not go beyond partintioning.On the partintioning page there is three option and none of the works.

When tried with 6.06 64-bit it hans with a blue screen

Can some one help me please?

What cd image did you download. The livecd, server, or alternate image? Did you check the md5sum?

---

### Post by Pamir on 2006-07-26
well, the image I downloade was: PC (Intel x86) server install CD.

How to check Md5sum?

---

### Post by Pamir on 2006-07-28
I have chekec the download there is no defect on it.

Can some one help me please?

---

### Post by Kilz on 2006-07-28
> **Pamir said:**
> I have chekec the download there is no defect on it.

Can some one help me please?

Did you chek the cd to make sure it burned corectly? If so what graphics card do you have?

---

### Post by Pamir on 2006-07-31
well, there is no problem with CD, seems that instaler can not seem PCI plug in sata raid controler and subsequently the Hard drive. I have tried with original CD and the one I burned.

---

### Post by drn8 on 2006-08-01
I would suggest not using ubuntu, their sata support seems rather poor at the moment x.X, try another distro.

---

### Post by Pamir on 2006-08-02
Well have tried debian, Knopix sofar. I will have a go at suse and redhat,

---

### Post by balaram on 2006-08-02
Do you also have a PATA hard drive in your computer? Dapper won't recognize my SATA drive if I have a PATA drive installed. I disconnect the PATA's install OS and then plug in PATA's. OS will then recognize both PATA's and SATA. I have an AMD64 CPU and a Biostar mobo.

---

### Post by AllenGG on 2006-08-02
> **Pamir said:**
> Well have tried debian, Knopix sofar. I will have a go at suse and redhat,
Please let us know how you fare with the other "Distros", personally I've had no problems with my S-ATA drives, designations SDA1, SDA2, SDB1 etc, showing as SD.  It was necessary to turn off the "promise" controller in the BIOS to satify my needs.

---

### Post by drn8 on 2006-08-04
It seems as of kernel 2.6.14 nforce sata was broken, [here](http://lists.debian.org/debian-kernel/2006/03/msg00422.html) is a debian bug report, other distros (gentoo,ubuntu,suse) seem to have expierenced the same problem. While this shouldnt effect your sata card, it explains my issues.

---

### Post by dbw on 2006-08-04
I also have a SATA II system, and the install process seems to hang.  I was able to get through this by typing:
```
evms_activate
```
followed by CTRL-D, as suggested in [this thread.]("http://ubuntuforums.org/showthread.php?t=186115&referrerid=48700")
This got me through the installer.  Note that I typed this several times (due to my frustration at it not working), sometiemes followed by ENTER, and sometimes not.  I then stood up, and when I came back, the initial install stuff had finished perfectly.

---

### Post by Pamir on 2006-08-23
Hi everyone,

Well after so I finally installed Opensuse 10.X on the server it worked. I am still thinking of installing Ubuntu, but don't to solve the problem. I found this site [http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html) and it is talking about patches and rebuilding the installer. I don't know to go about it. 

Would it be better to make a floppy driver or rebuilding the installer?

Can some one guide me please?

Thanks

---

### Post by dbw on 2006-08-23
@Pamir -
  did you try using the standard Ubuntu installer, and the [control]-D trick that I suggested?  You really should not have to rebuild the installer - I have 2 SATA-II drives running in RAID-1, and everything worked fine.

---

### Post by hitekhal on 2006-08-23
it may be motherboard dependent.
tried installing ubuntu on an ecs motherboard and it would not play nice with my sata drive.
installed on a gigabyte motherboard smooth as 12 yr old scotch.

cheers

---

