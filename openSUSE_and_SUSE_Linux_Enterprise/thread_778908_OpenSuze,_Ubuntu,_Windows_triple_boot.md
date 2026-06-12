---
title: "OpenSuze, Ubuntu, Windows triple boot?"
date: 2008-05-02
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Metallion on 2008-05-02
Hello there, I've recently taken a liking to Opensuze but I'm not sure if I really want to make the switch from Ubuntu. I was wondering if anyone has installed them as a dual boot before or a triple boot including windows which would be my case.

If I install OpenSuze from the live cd will the newly installed Grub also find Ubuntu?

Thanks.

---

### Post by ibutho on 2008-05-02
I am not sure if it will automatically find Ubuntu, but you could make a note of your Ubuntu /boot/grub/menu.lst (maybe save a copy to a usb stick) and add the entries to the openSUSE grub if it does not auto detect Ubuntu.

---

### Post by Incense on 2008-05-04
Like any modern distro, it should have no problem finding your ubuntu and windows partitions. I have triple booted Ubuntu, SUSE, and windows in the past and had not problems.... other then wondering why I was booting three operating systems. :)

---

### Post by shuttleworthwannabe on 2008-05-17
I beg to differ, I just installed Suse 11 b3 on a dual boot system: WinXp and mandriva; unfortunately, the mandriva was not detected during grub installation. requires manual installtion, which I am not sure how to do.

---

### Post by Kevbert on 2008-05-19
If you're using two or more hard disks you may find that the bootloader does not work correctly.  It depends on the order in which you install the OS.  Having tried this (I now have 5 OS over 2 SATA drives) and mucked up my grub and fstab files, the best way seems to install XP first, then openSuse/Fedora (etc) and then finally one of the Ubuntu flavours.
If not performed in this order the partitions (which seem to be renumbered) and the UUIDs (Partition IDs in fstab renumbered) will not be recognized.
On a single drive this does not seem to be a problem.

---

