---
title: "[SOLVED] Installer can't see my partitions"
date: 2008-06-03
forum: x86 64-bit Users
---

### Post by aatiis on 2008-06-03
As usually, I set up my HDD before installing Kubuntu. I have 4 primary partitions:
[LIST=1]
[*]swap (**sda3**)
[*]/ (**sda4**)
[*]/media/data (NTFS) (**sda1**)
[*]/media/winxp (NTFS) (**sda2**)
[/LIST]
The problem is, my installer (kubuntu-kde4-8.04-desktop-amd64) doesn't see any partitions. Just wants to clean up everything on the drive (which wold be probably the best, but unfortunately I need the Windows XP, since other people use my laptop too.)
I can mount these partitions manually and use them with the live cd, only the installer can't see them. I don't see any command line options for the installer regarding the partitioning.
I tried with the Linux partitions removed (left the space unallocated for the installer), the result is the same. I haven't had this problem with any previous releases.

Is there a way to force the installer to use /dev/sda4 as the root filesystem? I could add the swap partition later...

Thanks for all your answers.

---

### Post by kebes on 2008-06-03
Can you be more specific about what "can't see" means?

When you get to the partitioning phase, you should have options like "Automatic", "Guided", and "Manual". The first two options may suggest to completely format the hard drive. However, if you go to the third option, you should see the layout of your hard drive(s) and partitions. From there, you can manually assign which partition to use for root, swap, etc.

So, I guess the question is: do the correct partitions show up in the manual partitioning section? If so, then partition that way!

---

### Post by aatiis on 2008-06-03
I recall having only two options. One guided (ereasing my whole HDD), and one manual. I remember having those three options in the previous releases, but KDE4 Hardy doesn't seem to have three options, only two.

My problem is, the second option (manual partitioning) doesn't show any of my partitions. Seems like it can't see my partition table. I can't edit or do anything other than creating new partitions. It shows my HDD as a blank one, without any partitions on it, even though I can use, mount and umount them in any console. I hope I was more specific this time.

So the problem is, I cannot allow the installer to wipe out all the data on my drive.

Any suggestions?

PS: I have an 80 GB parallel ATA HDD in my HP Compaq nx6325 notebook, assigned to /dev/sda. Feisty and Gutsy didn't have any problems with it. If nothing else, I could install Gutsy upgrade to Hardy and then switch to KDE4. But it seems easier to simply install the KDE4 Hardy.

---

### Post by Sef on 2008-06-03
Applications > Accessories > Terminal

Could you copy and paste the results of this code:

```
sudo fdisk -l
``` Small L.

It will show the partitions.

---

### Post by kebes on 2008-06-03
> **aatiis said:**
> I could install Gutsy upgrade to Hardy and then switch to KDE4. But it seems easier to simply install the KDE4 Hardy.
You could also try installing the "normal" version of Kubuntu 8.04 (Hardy) (which has KDE 3.5). Maybe this is just a bug in the KDE4 build of the install disk. It's easy to add KDE4 after the installation.

Or try booting the "alternate" install CD and see if it recognizes the partitions.

---

### Post by aatiis on 2008-06-03
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x93be93be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            1527        7562    45632101    7  HPFS/NTFS
/dev/sda2   *        7563       10338    20979945    7  HPFS/NTFS
/dev/sda3               1         139     1050808+  82  Linux swap / Solaris
/dev/sda4             140        1526    10485720   83  Linux

Partition table entries are not in disk order
```

I have two screenshots for you too.

---

### Post by fjgaude on 2008-06-03
Gosh, this must be a KDE4 issue because with Gnome the installer is good, very good, better than ever now that 8.04 is out. I can ask for nothing more. But I only see drives with the ability to creates Secondary partitions...

The only thing I can think of is that installing onto a partition Ubuntu likes to put a swap space, create Secondary partitions and the like. If it sees only Prime partitions it might not know what to do. Very complicated, as we all know, for it has taken this long to get to where the installer is.

---

### Post by aatiis on 2008-06-03
Right, but I have tried it with only the two NTFS partitions, and the rest of the place left unallocated. I suppose I'll install the kde3 version and upgrade to kde4. Thanks anyway.

---

### Post by Sef on 2008-06-03
The Windows OS should be on the first partition.  That may be causing some of the problem.

---

### Post by aatiis on 2008-06-03
Well, it did work with the previous distros, as long as Windows is on a primary partition... Should I move or clone it now?

---

### Post by aaron.d on 2008-06-03
> **aatiis said:**
> ```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x93be93be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            1527        7562    45632101    7  HPFS/NTFS
/dev/sda2   *        7563       10338    20979945    7  HPFS/NTFS
/dev/sda3               1         139     1050808+  82  Linux swap / Solaris
/dev/sda4             140        1526    10485720   83  Linux

Partition table entries are not in disk order
```

I have two screenshots for you too.

This may be a stupid question, but are you absolutely sure you selected the manual option for formatting?

IF so, from the second screenshot, the fact that it is only showing sda, and the only creation option is to make a new table, would indicate that the installer cant read the partition table. This is most likely a bug, since fdisk shows it fine.

I would try:

1) another install disc, preferably the default Ubuntu 8.04 one.


---- do this at your own risk ----
2) In the case that it's some weird, intermittent corruption, you COULD try using fdisk to rewrite the table. This could result in a loss of data, should anything screw up. But I think even running fdisk and making no modifications, then (w)riting before quitting might re-write the partition table.

---

### Post by aatiis on 2008-06-03
There's definitely something weird going on. I just downloaded **kubuntu-kde4-8.04-alternate-amd64.iso**, and it shows the same blank partition as the graphical one. There might be an error with my partition table?!

Anyway, **aaron.d**, could you please tell me how to re-write my partition table without modifying it? I'm not used to fdisk. I had a gparted live cd, but it's not here right now, I'd like to have my system up and running by tomorrow...

Thanks for all the help.

---

### Post by aaron.d on 2008-06-05
Please, try the default UBUNTU cd. 

I find it weird that fdisk shows you a partition table, yet you get nothing in the installer.


I forgot to ask, can you boot the windows system that is on that drive?
If so, then it might be be a bug in the installer. 

Also, looking at your partition table it seems like you partitioned this right from the start to be a linux system. You first partition is swap?
Can you give me a bit5 of background on how you set the system up?

About re-writing partition tables, as i said before: 

"I think even running fdisk and making no modifications, then (w)riting before quitting might re-write the partition table."

so that would be:

```
sudo fdisk /dev/sda
```


then while in fdisk, press 'p' to print the partition table (make sure it still reads it fine), then 'w' to write the partition. Should reboot after this to make sure the loaded kernel (from livecd) picks up the changes.

PLEASE NOTE THAT THE ABOVE IS POSSIBLY VERY DESTRUCTIVE.

I take no responsibility for damage to the fs, I am only assuming this will re-write, I have never had to do this, nor can I find documentation that says whether or not 'fdisk' will re-write the partition table EVEN IF no changes are made.

---

### Post by aatiis on 2008-06-05
Thanks **aaroon.d**, I'll give it a try.

By the way, I tried 'PTDD Partition Table Doctor 3.5', and it reports me an error, but fixing it wipes out all the partitions other than my C: drive.

I used to use only Linux on my notebook, but then I needed a pieceof Windows XP to demonstrate an enormous automotive program. As my VMware was eating up more and more of my 80 Gb HDD, I split a small space at the end of my drive to set up a real XP. A few weeks later I needed more space on my Windows, and so I deleted my Gutsy :(

Anyway, now I don't need the XP any more, and I'd like to try out KDE4 (I've been trying all the beta's), but I need the windows until I set up the USB ADSL modem on my Kubuntu (SAGEM Fast 840/800 IV, using the eagle e4 firmware and ueagle-atm). I didn't have a swap partition on my totebook, since I have 2 Gb RAM. That should  be enough for me, and I don't want to sacrifice 2 Gb of my HDD for hybernation.

I usually place the swap partition after my root partition. Is it better to do so, or should I start with swap?

I'll try to fix this problem with fdisk, and if it doesn't work, I'll burn a bunch of dvds and wipe out the whole thing.

---

### Post by aatiis on 2008-06-05
I've fixed the error by cloning my C: partition, enlarging it and copying all my data from D: to C:, then removing D: and making extended partitions for linux. Thanks for al the support.

---

