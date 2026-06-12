---
title: "Can't write to my external hard drive"
date: 2007-05-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by diddler on 2007-05-26
Ok, need another hint.  I have an external hard drive (USB 2.0) with NTFS formatting.  I have installed g3 on my system and it allows me to write to my internal NTSF drive without a problem.  I have set the options on g3 to allow me to write to external drives, but I still cannot.  Any suggestions?  If it makes a difference, I rarely boot up with the external drive connected.

---

### Post by Alex-Mcedonia on 2007-05-27
I have the same problem with my seagate 250gb :(

---

### Post by diddler on 2007-06-01
Oddly enough, the external hard drive suddenly developed the ability to write to the drive.  Not really sure what I did.  I think I just toggled the setting on and off a few times.  Strange.

---

### Post by morghi76 on 2007-06-02
I installed the NTFS-3G support using automatix. At the beginning I also experienced some issues... but after a reboot everything worked well. Even though with linux you don't have to reboot as often as with XP, sometimes it's worth doing it :D

---

### Post by diddler on 2007-06-03
> **morghi76 said:**
> I installed the NTFS-3G support using automatix. At the beginning I also experienced some issues... but after a reboot everything worked well. Even though with linux you don't have to reboot as often as with XP, sometimes it's worth doing it :D

Tell me about it.  My main problem with that (just as with XP) is that I am on dial-up so I have to shut down my connection, re-boot, then TRY to reconnect.  I realize that it is not Linux's fault that I live in the third world (i.e. the Southern US) but it is still irritating.

---

### Post by morghi76 on 2007-06-03
Ok, here is my story:

everybody is talking of Automatix as the perfect tool for the beginners. Therefore, right after the main istallation of the OS I downloaded and installed Automatix and went through all its options.
I selected NTFS support with NTFS-3G (among others)  but I didn't do my homeworks: I did not read about the software, I just clicked and installed it. Before that my externatl USB2 drive (250GB) worked out of the box (of course with no automatic write capability), but after automatix it did not. So I unistalled the software (always via automatix) and installed again, this time considering that:
for automatix to add the correct lines in fstab the USB drive has to be connected when you start the installation of the NTFS-3G
it's better to reboot once the installation is done
This time NTFS-3G worked great!
By the way, in case you don't want to use automatix, have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=217009]("http://ubuntuforums.org/showthread.php?t=217009")

---

