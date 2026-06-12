---
title: "Help!  XP no longer recognized after fresh install of Ubuntu"
date: 2008-12-22
forum: x86 64-bit Users
---

### Post by rodzlinux on 2008-12-22
Hello all,

I'm new to linux and just recently installed Ubuntu 8.10 on my PC.
Specs are as follows:

M/B: Gigabyte GPA EP35 DS3L
CPU:  Intel E2180 OC'd to 3.2 Ghz (Stable in windows for ~6 months)
Sound card: on-board Intel HDA something or other
Video card: MSI Geforce 8800 GTX 512 MB
RAM:  2 gigs of G.Skill F2-6400CL5D-2GBNQ
HDD: Western Digital 7K 8M SATA2 WD2500AAJS
500W PSU

I've had dual boot systems before, just never with linux.  When prompted which partition to use, I chose the "Guided" option that used the original xp partition and then allotted the rest of the HDD for linux.  It took a really long time to partition, and gave some error when it finished (can't remember).

I then created a swap partition of 4 gigs, and a mount partition for ubuntu to install.  Install went smooth from there, only problems are that I can't boot XP anymore, I have no sound, and I can't even mount the old XP partition in wine.  It gives an error that suggests running chkdsk, but I don't seem to have that program under linux. 

I'm working on the sound problem, but am having trouble finding info regarding the dual boot.  Any suggestions are greatly appreciated.  Thanks in advance for your time!

---

### Post by Yellow Pasque on 2008-12-22
> It took a really long time to partition, and gave some error when it finished (can't remember).
:\ I hope your critical data is backed up.

"chkddsk" is a Windows program; mount is suggesting you use your Windows CD to check the NTFS partition. If your NTFS partition wasn't shutdown properly or has other errors, this could cause problems.

Are you able to mount the NTFS partition from a LiveCD environment? (Make sure ntfs-3g is installed).

---

### Post by rodzlinux on 2008-12-22
Thanks for the suggestion.  I haven't tried mounting the windows partition from the LiveCD.  I'll try this soon as I get home tonight.  

Also, does it matter if I have an NTFS partition?  I think I may just have had a 32-bit windows partition.  Could that also be why it won't recognize it?  (I installed the 64-bit version of Ubuntu.)

---

### Post by Yellow Pasque on 2008-12-22
Unless you upgraded from an earlier Windows version, you most likely have an NTFS partition. Any reasonably modern Linux distro should recognize and read NTFS partitions, and I believe Ubuntu now comes pre-installed with ntfs-3g (read/write).

---

### Post by rodzlinux on 2008-12-22
Alright, so I ran chkdsk from the Windows XP recovery module and it found 1 error.  It didn't give me any other info.  Any ideas?

EDIT:  I am now able to mount the XP partition under wine, but cannot boot into windows.  Will I need to re-install windows or is there some way to get my computer to boot XP?

EDIT 2: I ran chkdsk again and it found no errors.  I still can't select XP as a boot option with grub tho.

Thanks again for your help!

---

### Post by Sef on 2008-12-22
Download [Super GRUB Disk ]("http://supergrubdisk.org")and reinstall grub.

---

### Post by caljohnsmith on 2008-12-23
> **rodzlinux said:**
> Alright, so I ran chkdsk from the Windows XP recovery module and it found 1 error.  It didn't give me any other info.  Any ideas?

EDIT:  I am now able to mount the XP partition under wine, but cannot boot into windows.  Will I need to re-install windows or is there some way to get my computer to boot XP?

EDIT 2: I ran chkdsk again and it found no errors.  I still can't select XP as a boot option with grub tho.

Thanks again for your help!
In order to get a clearer picture of your setup, how about opening a terminal in Ubuntu (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your problem might be.

---

### Post by rodzlinux on 2008-12-23
Thanks for all the helpful replies everyone!

I've almost got everthing worked out.  I burnt a super grub iso and was able to boot into windows from there.  I didn't have enough time to figure out how to re-install grub, but I'll work on that tonight after work.  (There's a lot of info on that CD and I was reading up on the tutorials contained on it.)

Now I just need to figure out how to get sound working.  I tried following the directions in Temüjin's sig, but still couldn't any sound.  I'll post a new thread for that.

---

### Post by rodzlinux on 2008-12-23
EDIT: sorry double post

---

### Post by rodzlinux on 2008-12-24
Alright, so now I'm able to boot windows xp from the super grub disk, but when I do that, I can no longer boot into Ubuntu.  The only way for me to get Ubuntu to boot is if I repair grub with the Super grub disk.  Is it not possible for me to be able to choose XP vs Ubuntu through grub?

---

### Post by logos34 on 2008-12-24
> **rodzlinux said:**
> Is it not possible for me to be able to choose XP vs Ubuntu through grub?

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu)

---

### Post by caljohnsmith on 2008-12-24
Sure, you should be able to boot Windows from your Grub menu, you'll just need to add an entry for Windows in your Grub's menu.lst file. If you would like a hand figuring out what the correct entry should be, please post the contents of the RESULTS.txt file from that script in my previous post, and I'll be glad to help out if you want.

---

### Post by rodzlinux on 2008-12-24
Thanks for the link, I'll try that out soon as I get home.  A side problem I've noticed when booting windows from the grub disk is that my time/date settings get advanced exactly 8 hours.  Not a big deal, but hopefully it goes away when I add the windows entry into my menu.lst file.  (that's an "L", not a "1", correct?)

---

### Post by Sef on 2008-12-25
> when I add the windows entry into my menu.lst file.  (that's an "L", not a "1", correct?)

That is correct.  It is an L.

---

### Post by rodzlinux on 2008-12-28
Thank you to everyone in this thread that helped me out.  I finally got windows to boot from grub without the disk.  (Got it to work a few days ago, but I've been out of town on a snowboarding trip so I couldn't post.)

---

