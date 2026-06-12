---
title: "LiveCD Can't see my harddrive"
date: 2008-11-24
forum: x86 64-bit Users
---

### Post by Izek on 2008-11-24
In the prepare partitions step, kubuntu liveCD cannot see any available drives or current partitions. However, in the liveCD, when I go to root/media, disk (my 500 GB SATA Drive) can be browsed.

How do get the installer to see "disk"?

---

### Post by Bucky Ball on 2008-11-24
Do you have free disk space for Kubuntu to install itself?

---

### Post by Izek on 2008-11-24
> **Bucky Ball said:**
> Do you have free disk space for Kubuntu to install itself?

See for yourself.

---

### Post by sambarusty on 2008-11-24
I had a similar problem myself with the SATA drive.  One of the recommendations I found during my search was to set pci=nomsi during the installation process and at the boot sequence.  You need to hit F6 while installing and you can edit the boot line.  Otherwise it doesn't recognize some SATA drives. It didn't work for me, but it seemed to work for many others.  May be something to try.

---

### Post by Izek on 2008-11-24
Then I think I'll stick to gnome-based distros, I was hoping to use kubuntu for a while, but it looks like it's a no go, especially with how flash won't install into the liveCD (I can't even send the problem report on why it didn't, the upload gets stuck.) KDE also seems slower than gnome to me. Konquerer also has several drawbacks to firefox it seems. I also don't really care for playlist based music players either. So totem's good for me.

---

### Post by Bucky Ball on 2008-11-24
Strange. But other installers pick it up fine? You seem to have installed something else already so guessing so. Have you tried the alternate install disk of kubuntu? This could be the cd itself.

Sounds like gnome is a better match for your requirements anyhow. KDE is slow and buggy on my machine and a little too lush for me (bit of a minimalist). You may have done this, you can always load kde (without the whole kubuntu install) and select to boot into that at the login page. I have icewm, openbox, kde and a couple of others which I can boot into. Gnome-Openbox suits me fine and KDE never gets used. Good luck.

---

### Post by tvtech on 2008-11-24
I had a problem with changes in the installer from 7.04 to 8.04 It changed how it recognized my IDE  SATA  and SCSI controllers.  it's a 3ware sata controller and an adaptec scsi controller.  it forced the Sata controller to be SDA1  which borked grub and made the whole install defunct because grub still insists that my IDE is hda1.  The long and the short is I had to do an upgrade and couldn't do a fresh install.  Good thing I still had my 7.04 image laying about on my hdd and a dvd rom and cd burner and a little knoppix laying about for good measure otherwise I'd have been dead in the water. I"m sure there's away around this, but I just ran out of time.

---

### Post by Bucky Ball on 2008-11-24
Got ya. Can you post the results of:

nano /boot/grub/menu.lst

... please?

---

