---
title: "Please help a Newb"
date: 2006-02-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by BRuhling on 2006-02-07
I am running an AMD X2 4200+ on an ASUS A8N-SLI Premium mobo with dual EVGA 7800GT video cards.  My hard drives consist of a Maxtor 250GB SATA drive with Windows installed natively and a new Maxtor 160 GB SATA that I installed Ubuntu 5.10 on last night.  The install appeared to run properly, but when I go to boot up, it gives me a boot error.  If I hit F8 to go into the Boot Directory and tell the computer to boot from the 250GB drive, the grub loader comes up properly.  Is there a fix to this problem?

Thanks,
  Bill

---

### Post by wallijonn on 2006-02-07
It sounds as if you installed the boot loader (GRUB) through the first disk's MBR instead on on the 160GB's root. 

You'd proably have to go into WXP Recovery console, [COLOR="Red"]fixmbr[/COLOR], [COLOR="Red"]fixboot[/COLOR], then re-install GRUB onto the second hard disk's root (instead of choosing MBR).

---

### Post by BRuhling on 2006-02-07
First, thanks for your response.  Second, can you explain that to me in more basic terms.  Other than having installed Ubuntu, I know nothing about Linux.

---

### Post by jon_gunnar on 2006-02-08
[QUOTE=BRuhling]I am running an AMD X2 4200+ on an ASUS A8N-SLI Premium mobo with dual EVGA 7800GT video cards.  My hard drives consist of a Maxtor 250GB SATA drive with Windows installed natively and a new Maxtor 160 GB SATA that I installed Ubuntu 5.10 on last night.  The install appeared to run properly, but when I go to boot up, it gives me a boot error.  If I hit F8 to go into the Boot Directory and tell the computer to boot from the 250GB drive, the grub loader comes up properly.  Is there a fix to this problem?
  Bill[/QUOTE]

Sorry to ask, but would'nt the easiest fix be to set the computer up to boot from the Maxtor disk then?
U can choose the windows install from the grub menu when it starts I presume? My impression is that the preferred method is to install grub to the mbr.

And I would highly recomend to have a look in the wiki at [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)
and more specific for grub:
[https://wiki.ubuntu.com/GrubHowto?highlight=%28grub%29](https://wiki.ubuntu.com/GrubHowto?highlight=%28grub%29)
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub)

And one other thing,its much better if you use the subject to describe the problem you got.That you are a newbie does not say so much really. A lot of people just reads the subject to see if there is something they can help with or not.No offense meant,just an advise

---

