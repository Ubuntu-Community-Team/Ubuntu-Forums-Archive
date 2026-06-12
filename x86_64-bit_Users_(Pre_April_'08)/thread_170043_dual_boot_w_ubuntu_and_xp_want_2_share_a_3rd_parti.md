---
title: "dual boot w/ ubuntu and xp want 2 share a 3rd partition"
date: 2006-05-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by dead7iest-weap0n on 2006-05-03
OK, If I were to have a 3rd partiton ,or make it the 4th (grub), could I share it w/ xp and ubuntu. If I can, how owuld i go about doing it?
Thanx in advance!

---

### Post by teasum on 2006-05-03
I put together a dual boot system with an ext3 partition for Ubuntu, NTFS for XP, and a shared FAT32 partition.  However, I did have some issues with diskcheck removing some recently created files.  But that is one option.

Another option is to use an ext2 or ext3 partition and then install a utility in XP that will allow it to access your ext3 partition.  Try this link:

[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

There are pros and cons either way, which someone more knowledgable than me could probably explain.  Let me know which route you go, and how it works out.

---

### Post by dead7iest-weap0n on 2006-05-03
hmm, well im only using the partition for music, and media files, so would there be problems regarding permissions, becuase im constantly ading new media.

---

### Post by teasum on 2006-05-03
In that case, a shared FAT32 partition should work.  It depends on how exactly you plan to use it.  In other words, if you will read from and write to it from both XP and Ubuntu, FAT32 is your best bet.  If you will only add media from XP, you could even share an NTFS partition.  Or, if you only add media from Ubuntu, ext3 + the utility I mentioned would work.  

These are just the options, however.  I used a FAT32 partition and it worked fine... that is until I had a bad crash, and when the file system was checked I lost a bunch of files.  (Well, not really lost, but recovered as .chk files, which are a pain to sort through... but that's another story.)  That's my experience.  Good luck!

---

### Post by new2linux on 2006-05-04
Just to throw in my experience with this...

I dual-booted xp and ubuntu on an 80 gig hd.  I gave XP 10 gig(NTFS), Ubuntu 10 gig (this included swap etc.),  I then set the remaining 60 gig as Fat32.

I ran the system like this for quite a while and never had any problems.  It was nice to be able to get the different systems to interact.  I used the FAT32 for music storage, video storage, and basically anything else you use a hard drive for

For what it's worth...

---

### Post by dead7iest-weap0n on 2006-05-04
how exactally would I format the fat 32 drive?

---

### Post by turbojugend_gr on 2006-05-06
Hi there,
First of all I experienced the same problems with the "above" users regarding data loss.

Anyway you can follow the instruction HERE to format a partition/disk over 32gb with vfat (FAT32) [http://www.ridgecrop.demon.co.uk/index.htm?fat32format.htm](http://www.ridgecrop.demon.co.uk/index.htm?fat32format.htm)
or create a smaller or equivelant to 32gb partition (through My computer->Device manager->Disk manager or something) inside Win XP and format it with fat32. Size limitation only prevents windows xp from formating with fat32 not managing a disk.

After you have a working under XP vfat disk you can edit the /etc/fstab file to gain full useability of your new partition. You can learn how to do so by reading the manuals for mount and fstab (in a terminal type man fstab, man mount) and by reading some other threads in this site of the same content. You can also follow the instruction of the ubuntu official site's user guide on Windows Partitions found here [http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html).

Please let me know if i was helpfull.

---

### Post by Lin-X on 2006-05-07
I dual boot Win98 and Ubuntu and have a shared partition that is formatted as Fat32. I used gparted from a Knoppix live cd to make that partition; no problem about "how" to do it because gparted gave me choices. You know if you try it and it
doesn't work out, you can always undo it. I mean, it's not a permanent thing. I thought it was super simple and easy when I did it. I'm pretty sure you could use a Windows program like Partition magic to do it too. I wish you luck but really don't think you need it. Just try it and you'll see how easy it is.

---

