---
title: "NTFS wont show or any of its partitions"
date: 2008-06-07
forum: x86 64-bit Users
---

### Post by hristiyan on 2008-06-07
Xp's installed on the first hdd, xubuntu on the second (they're quite identical), except now that i've found the version of linux that i want to use, it wont show the NTFS hard drive, or the fat32 partition on it.

When i type in df -h, i get
/dev/sdb1             182G  2.5G  171G   2% /
varrun                503M  100K  503M   1% /var/run
varlock               503M     0  503M   0% /var/lock
udev                  503M   72K  503M   1% /dev
devshm                503M     0  503M   0% /dev/shm
lrm                   503M   43M  461M   9% /lib/modules/2.6.24-18-generic/volatile

now i don't see the other hdd, just the one xubuntu is installed on...  tried the file manager, but it wont show it to me...  i've tried the following commands (from a search on the problem, but no go)
sudo mount -t ntfs /dev/sda1 /media/windows
sudo mkdir /media/windows
but nothing...  this one seems interesting though, from the following command
mousepad /etc/fstab
# /dev/sdb1
UUID=61809dd6-3ab5-4615-ba3b-e3a1a9e899bc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=ad667c16-da2b-4d58-9797-6892b56227cd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Just to be more spesific, i use Hardy Haron, i've updated it, have a 64 bit 3500mhz - 1024 ram - 128 meg ATI Radeon card

---

### Post by Kilz on 2008-06-07
> **hristiyan said:**
> Xp's installed on the first hdd, xubuntu on the second (they're quite identical), except now that i've found the version of linux that i want to use, it wont show the NTFS hard drive, or the fat32 partition on it.

When i type in df -h, i get
/dev/sdb1             182G  2.5G  171G   2% /
varrun                503M  100K  503M   1% /var/run
varlock               503M     0  503M   0% /var/lock
udev                  503M   72K  503M   1% /dev
devshm                503M     0  503M   0% /dev/shm
lrm                   503M   43M  461M   9% /lib/modules/2.6.24-18-generic/volatile

now i don't see the other hdd, just the one xubuntu is installed on...  tried the file manager, but it wont show it to me...  i've tried the following commands (from a search on the problem, but no go)
[B]sudo mount -t ntfs /dev/sda1 /media/windows
sudo mkdir /media/windows[/B]
but nothing...  this one seems interesting though, from the following command
mousepad /etc/fstab
# /dev/sdb1
UUID=61809dd6-3ab5-4615-ba3b-e3a1a9e899bc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=ad667c16-da2b-4d58-9797-6892b56227cd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

did you create /media/windows before trying to mount sda1 in it? Buy the listing of the steps it looks like you did it after. Are you sure the ntfs partition is sda1?

---

### Post by lisati on 2008-06-07
Have you installed NTFS-3G?

---

### Post by hristiyan on 2008-06-07
Thank you for the replies
Sorry, i didn't do it backwards, just posted it backwards, i tried it again, i just looked into media and i can see the windows folder containing the first ntfs partition, but i can't find the second partition, or the other 2 on the first hard drive...  how would i be able to add them?

i haven't installed NTFS-3G, i'll try looking for it in the add/remove software and synaptic...  i found it in synaptic, it's already installed, but i'm unsure of where to find it or how to use it

---

### Post by hristiyan on 2008-06-09
I just inserted the xp cd inside the DVD drive, and a non-default file manager popped up (Nautilus) which can see all partitions (except one).  It seems that the default Xfce file manager is Thunar (which doesn't seem to display other partitions by default).

Could anyone tell me how i can make the Nautilus as the main/default file manager, and possibly a way for me to access it without having to insert the xp cd, for it to pop up?

Alright, i figured it out, i right clicked on the desktop, then Create Launcher, then Nautilus, which fixes the (I can't see NTFS partition, or other partitions)

Would anyone be able to point me in the right direction as to setting up Nautilus as the default file manager? possibly without having to use GNOME (if it's possible)

---

### Post by Jouke74 on 2008-06-10
Did you install Xubuntu the right way? Meaning that you told the partitioner to keep the NTFS partitions and mount them at various points media/etc?  I am quite sure you did not.

Your NTFS partitions are not in your Fstab, therefore you need to add them in your Fstab manually now. No need for a re-install.

See: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

After you can reach them from a terminal, you might still need to adjust the desktop icons in the desktop settings of the XFCE manager to include all drives.

Finally, you inserted the **XP** CD in the CD drive and that it showed Nautilus???? There is no way Windows could show Nautilus, although I would love to see that some day :lolflag: The (X)Ubuntu live CD which you more likely used simply mounts all available partitons read only, hence you can see them. If you really inserted a XP cd then you have a more interesting problem, meaning that you probably have multiple Ubuntu desktop environments installed. 

Thunar is the quite capable file manager of XFCE. Showing NTFS partitions is for sure not taken out.

---

### Post by hristiyan on 2008-06-11
I don't think that i told the partitioner to keep the NTFS partitions and mount them at various points (new to linux).  Thank you for helping me solve this problem.

---

### Post by Bennett2005 on 2008-06-11
I'm having a similar problem.

Upon booting into Ubuntu recently, my regular mounted /windows NTFS partition is as good as gone.  The directory isn't listed in the file system anymore.  I can't connect to my other NTFS partition either.

Furthermore, my /home folder, also on it's own partition, is apparently gone as well.  I have a /home, but it no longer contains any of the data I had saved there, nor does it contain the links I had set up to access my /windows ntfs partition either.

I"m running an AMD64 4.2, 2 gig ram, 160HD, ATI 128mb vid card.

---

### Post by Jouke74 on 2008-06-12
@ Bennett2005 
Anything special you did to make that happen? /Home and NTFS partiotions gone sounds like bigger trouble. Did you add a harddisk or so?

@hristiyan
Is it really solved now completely? If so very good, glad to help. Otherwise just write the remaining issues.

---

### Post by hristiyan on 2008-06-15
Jouke, it is really solved.  I appreciate everyones help (strange how there's a solution for linux, yet only software for windows)
Thank You :KS

---

