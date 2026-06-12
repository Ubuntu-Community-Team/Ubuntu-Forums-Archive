---
title: "NTFS partitions. Where are they in 8.10?"
date: 2008-11-15
forum: x86 64-bit Users
---

### Post by C. Wizard on 2008-11-15
I'm using Kubuntu 8.10 amd_64.

The short version. Is there anyway to access the NTFS partitions other than using Dolphin?

The long verson. :)
In versions 7.04, 7.10, and 8.04, the NTFS partitions were listed (mounted) as subdirectories (folders) of the "Media" directory off of Root.  As such you were able to use any file manager to access them or you could work your way to them via the command line in a console. 
I was shocked to find they are no longer listed in fstab file and it appears the only way to access the NTFS partitions in Kubuntu 8.10 is to use, ugh, the Dolphin file manager.
Is there any other way to access the NTFS partitions?
Thank you.

BTW, I don't know if it is the Ubuntu developers or the folks at KDE, but I'm starting to notice a trend of hiding more and more of the system from the user.  Not the right direction to be moving in, IMHO.  I don't mind some of the hardware being automatically setup (sound, CD drives, graphic cards, etc.), but how I want to run my system is my business and I should have that option.  
This trend, plus making KDE 4.xx the default desktop when it is not anywhere near ready for daily use, is all starting to smell like that company from Redmond who has been using the public as beta testers for many years.  At least we are not required to pay for the "privilege.":)

---

### Post by iponeverything on 2008-11-15
I haven't noticed things getting hidden. Things have getting moved around since the beginning, this is not a bad thing -- putting together a OS is bit like playing tetris.  I think there does seem to be a push in Ubuntu to muck with all things root, seems to be almost obsessive at times -- but almost pointless when everyone gets into the habit of prefixing every command with sudo.  I get a bit of kick out of the people out there that seem to think that the solution to every problem somehow involves a recursive chmod and the perms 777. Anyway -- I have gone off onto a bit of tangent. You can still mount the ntfs volumes by hand, just create the mount point and mount them.

---

### Post by C. Wizard on 2008-11-15
> **iponeverything said:**
> ...You can still mount the ntfs volumes by hand, just create the mount point and mount them.
I would like to edit the fstab file and have them mounted at boot up so I don't have to do it manually.  Think it might work with this version of K/Ubuntu or will it choke?

I switched to Kubuntu from Slackware because, one, I was tired of doing things "manually" that I don't think a user should have to do at this point in the evolution of the personal computer, and, two, Slackware doesn't have "official" 64 bit version.
However, after having used various versions of Kubuntu for the last year or so and watching how they, the Ubuntu developers seem to be moving away from what I call the traditional Linux format, I'm pretty much decided to move back to Slackware.  There is a "unofficial" 64 bit version of Slackware called, "Slamd64," and as soon as I have a long weekend, and there are a couple coming up, I'm going to download the DVD ISO and do the installation.

---

### Post by Arup on 2008-11-15
Strange, in my case, right after install, my NTFS partitions were shown and they were writeable as well.

---

### Post by C. Wizard on 2008-11-15
> **Arup said:**
> Strange, in my case, right after install, my NTFS partitions were shown and they were writeable as well.
Shown where?
Thanks. :)

---

### Post by iponeverything on 2008-11-15
> **C. Wizard said:**
> I would like to edit the fstab file and have them mounted at boot up so I don't have to do it manually.  Think it might work with this version of K/Ubuntu or will it choke?

I switched to Kubuntu from Slackware because, one, I was tried of doing things "manually" that I don't think a user should have to do at this point in the evolution of the personal computer, and, two, Slackware doesn't have "official" 64 bit version.
However, after having used various versions of Kubuntu for the last year or so and watching how they, the Ubuntu developers seem to be moving away from what I call the traditional Linux format, I'm pretty much decided to move back to Slackware.  There is a "unofficial" 64 bit version of Slackware called, "Slamd64," and as soon as I have a long weekend, and there are a couple coming up, I'm going to download the DVD ISO and do the installation.


Mounting them via fstab will work just fine.

If you post a "fdisk -l" to list your partitions and identify the ones that you would like mounted and where you like them mounted. We can give you the lines you need for your fstab.

---

### Post by C. Wizard on 2008-11-16
> **iponeverything said:**
> Mounting them via fstab will work just fine.
If you post a "fdisk -l" to list your partitions and identify the ones that you would like mounted and where you like them mounted. We can give you the lines you need for your fstab.
Thanks for the offer, but that I can do. :)

Which brings up another question.  

In 8.04 you could tell, ugh, Dolphin to open a directory or a file as root. If it was a text file it would open an editor and you could edit and save your changes.
In 8.10 that option is no longer available and I have to open a console, change to root (sudo-s), and start an editor from the command line so I can edit and save the changes.
Anyway around this one?
Thanks.

---

### Post by Arup on 2008-11-16
> **C. Wizard said:**
> Shown where?
Thanks. :)

Right on places, my NTFS is labelled DATA.

---

### Post by C. Wizard on 2008-11-16
Thank you gentlemen.
I setup the fstab file just like I use to do
it in Slackware and now have access to the ntfs
partitions.
Thanks, again, for your help.

---

