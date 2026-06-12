---
title: "no option to shut down or restart"
date: 2008-05-19
forum: x86 64-bit Users
---

### Post by Mgiacchetti on 2008-05-19
I installed a dual boot system XP MCE / Ubuntu with ntldr as the boot manager, on one hdd partitioned for MCE (0) ubuntu (1)

I can select lock, hibernate, standby, logout, or switch user, but the only way that I can shutdown is to configure the power button to shut down automatically when i press it.  I cannot restart the machine at all in ubuntu.  

I am a new ubuntu user, installed once with little problems (xp mbr problems to be exact) and i am wondering if using NTLDR is the issue, because on my previous install, this problem didnt occur.

Although i havent installed any propritary software yet, (nvidia) as i cannot bring the system on the internet until tonight and i would rather not waste the rest of my day downloading depends and wasting cd-r's

Will update as the night goes on.
Any help will be greatly appreciated.

---

### Post by Sef on 2008-05-20
> I can select lock, hibernate, standby, logout, or switch user, but the only way that I can shutdown is to configure the power button to shut down automatically when i press it. I cannot restart the machine at all in ubuntu.

I am a new ubuntu user, installed once with little problems (xp mbr problems to be exact) and i am wondering if using NTLDR is the issue, because on my previous install, this problem didnt occur.

I would say that NTLR is the problem.  Windows boot loaders only recognize Windows.  Download [Super Grub Boot Disk]("http://supergrub.forjamari.linex.org/") and install GRUB.  That should fix that problem.

---

### Post by Mgiacchetti on 2008-05-20
actually it was just a bad install, i unplugged my cell phone from the usb port and reinstalled, no problem. (--please remove all removable media before setup--)  should detect that something is plugged in and tell you that having that device plugged in during setup might cause problems with Ubuntu.

Although now i can't mount the drive that has windows on it; and im almost positive its because i use NTLDR.  I am hesitant installing any type of grub to the MBR because of the problems i had before, if it messes up i have to F10 restore as i do not have a cd with xp mce on it and thats my only hope (this providing that my revocery partition is still recognized by the bios, if not, im gonna have to go through hacked windows installs, formats and multiple f10 reboots to get it to work.)

It's not that big of an issue for me right now, (the possible problems vs fixing the issue; not the fight i wanna see right now) but i hope this helps others that had/have the same problem.

---

