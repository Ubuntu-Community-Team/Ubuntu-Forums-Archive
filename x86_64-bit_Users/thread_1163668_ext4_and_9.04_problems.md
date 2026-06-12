---
title: "ext4 and 9.04 problems"
date: 2009-05-18
forum: x86 64-bit Users
---

### Post by 73ckn797 on 2009-05-18
I do not believe that ext4 is playing well. About every 4-5 reboots and the system will not load GDM. I have to run fsck to fix the corrupted files. All shut downs are normal. 

Is anyone else having issues? I actually know some are since I browsed the forums while writing this post. I do remember reading of a patch used with other OS's and that may have been built-in to Ubuntu. That I am not certain about. OH WELL!! what are a few nano-seconds anyway? Not much, HUH?

Good thing I also have 9.04 with ext3 on another drive and have no problems. It (ext4 + 9.04) is installed on a brand new drive. That was after an ext4 install corrupted the previous drive. That old drive, after running a zero HD format process, is working flawlessly in another computer. I think that I will wipe the ext4 drive completely and stick to what works for myself.

---

### Post by Arup on 2009-05-18
ext 4 here on all my Ubuntu systems, one Phenom, one dual quad core, phenom with nvidia 8400 card, dual quad with ati 4850 dual GPU and none have given me any problems.

---

### Post by bhishan on 2009-05-18
I installed ubuntu 9.04 in ext4 last week, no problems yet.

---

### Post by AndyCee on 2009-05-18
I had a problem with GDM when mounting an ext3 home partition from Jaunty installed on ext4 for some reason. I got around it by re-installing and editing fstab manually post-install, instead of during the install process.

I don't know if that helps at all...

---

### Post by Jimtheplanner on 2009-05-19
I've been wondering about ext4? I have Mandriva 2009.1 operating on ext4 without any difficulties so far that's with both Gnome & KDE installed. I was gonna install & duel boot Ubuntu Jaunty.

Would I be better if everything ran on ext3???

Jim

---

### Post by 73ckn797 on 2009-05-19
> **Jimtheplanner said:**
> 
Would I be better if everything ran on ext3???

Jim


That is what I am reconsidering. Some are having no problems so I cannot claim ext4 is bad. It is just not working out well for me. It may be something completely unrelated but I have not taken the time to run things down.

I will monitor other postings to see what others are experiencing.

---

### Post by dabl on 2009-05-19
Kubuntu 9.04 on ext4 has been running fine since the Beta was released.  I suspect your issue is with the booted video diplay, not the filesystem.

I previously had some challenges with the video boot option and KDM -- it was worse with 8.04 and 8.10, on my nVidia cards.  I see you have a GF 7900.  You might want to try "xforcevesa" and see if that lets GDM start more reliably.  It also relates to your monitor -- depends on what resolution you want to start GDM with.  I've previously needed vga=788 and vga=791 to get past both the boot splash and the greeter.

---

### Post by 73ckn797 on 2009-05-19
> **dabl said:**
> Kubuntu 9.04 on ext4 has been running fine since the Beta was released.  I suspect your issue is with the booted video diplay, not the filesystem.

I previously had some challenges with the video boot option and KDM -- it was worse with 8.04 and 8.10, on my nVidia cards.  I see you have a GF 7900.  You might want to try "xforcevesa" and see if that lets GDM start more reliably.  It also relates to your monitor -- depends on what resolution you want to start GDM with.  I've previously needed vga=788 and vga=791 to get past both the boot splash and the greeter.

I have not had this issue prior to 9.04 & ext4. I am using 9.04 & ext3 right now without a hitch.

---

### Post by Arup on 2009-05-19
On the boot issue with nvidia I have to agree there, with drivers installed of the repos and autologin enabled, system boots into functional Windows without any delay. With nvidia drivers installed via .sh from nvidia's site, there is a slight delay into getting the Windows to open.

---

### Post by peakpc on 2009-05-19
Is your Ext4 jaunty a fresh install or an upgrade from Ext3?  I have been using 64bit jaunty with ext4 (fresh install) dual boot with xp ntfs and a second ntfs drive to share sense it's proper release on my daily use laoptop and with the exception of a hick-up with the wireless (broadcom) it has worked well (with out problems related to Ext4).  However, I'm not trying to say that It can't brake.  just looking for clues.:)

---

### Post by 73ckn797 on 2009-05-19
> **peakpc said:**
> Is your Ext4 jaunty a fresh install or an upgrade from Ext3?  I have been using 64bit jaunty with ext4 (fresh install) dual boot with xp ntfs and a second ntfs drive to share sense it's proper release on my daily use laoptop and with the exception of a hick-up with the wireless (broadcom) it has worked well (with out problems related to Ext4).  However, I'm not trying to say that It can't brake.  just looking for clues.:)

The problem was occurring on several fresh installs and even burning a new disk. The md5's and LiveCD check passed on both disks.

Possibly the one issue that may be causing a problem from observation is that I have had to boot into Windows XP to use a program there. When in there I would need to go into my Ubuntu drive and get a file. Several times, or at least the last time, that I accidently clicked on the ext4 drive and not be able to read it ( I know the ext4 cannot be read from Windows ) that after that when I boot back into the ext4 drive, the issue seems to have re-occured. This also happened after being in the 9.04 & ext3 OS and trying to read the ext4 drive. I wonder if that is corrupting things.

What do you all think?

---

### Post by 73ckn797 on 2009-05-20
Another observation is that after I have had the above described problems, format of the the ext4 drive to ext3 using gparted does not fix things. I will format, perform a fresh install and upon reboot get the same errors I have mentioned. There have been multiple read errors on the drive when booting back into the ext3 drive as it tries to read the other drive.  I ran a zero pass disk wipe which seems to fix everything. I am hesitant to use ext4 again due to what seems to be a case where it corrupts the drive. That corruption is not fatal as the zero pass wipe returns info that it was successful and running fsck shows no errors. I even ran chkdsk through Windows and it returns no errors.

---

### Post by Endolith on 2009-05-20
Check your drive again.  Get smartmontools and do smartctl scan for errors, and do badblocks -nv to do a non-destructive test of every bit on the drive.  I've recently had a lot of trouble with this.  Drive has errors, tests fail, I format the drive and suddenly it doesn't have errors again, and tests pass, even the SeaTools test.  After running badblocks, though, it fails again.

---

