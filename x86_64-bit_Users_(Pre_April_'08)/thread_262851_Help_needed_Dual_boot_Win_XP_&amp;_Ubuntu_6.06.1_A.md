---
title: "Help needed: Dual boot Win XP &amp; Ubuntu 6.06.1 AMD64!"
date: 2006-09-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bunro on 2006-09-22
Help needed: Dual boot Win XP & Ubuntu 6.06.1 AMD64!

I would like to install Ubuntu 6.06.1 next to Windows XP on the following hardware:
Processor AMD Athlon64 3000+
Motherboard Asus K8V Deluxe/ Rev. 1.12
512 Mb Ram
HDD Maxtor 160 Gb 7200 rpm 8Mb SATA
Videocart ATI REDEON 9600SE

I have tried several things all non successful. At this stage when I install Ubuntu from disk
Desktop and/or Alternate the system stops after Starting Kernel log ...

At this stage I have deleted all Linux partitions and would like to here howto successfully install Ubuntu.

Hopefully there is someone that can help me out of this misery!

Regards, Robert

---

### Post by kick6 on 2006-09-22
Easy.  Intsall windows first.  When partitioning the disk, make sure to leave a nice fat chunk of space for ubuntu.

Install ubuntu in the leftover space.


You have to do it in this order or winbloze will hijack the MBR, and you won't be able to boot ubuntu.  its possible to fix it, but just install in this order, and you'l lbe fine.

---

### Post by Bunro on 2006-09-22
Kick6 thanks for your replay,

Windows XP is installed. And I tried (with Alternate disk) deleting/ formating/ creating partitions:
#1 primary	62.9 GB	k	ntfs	/media/sda1
#5 logical	52.5 GB	k	ntfs	/media/sda5

/swap 1024 MB 	logical		etc3
/ (root) 10GB		primary	etc3
/home 37.5 GB	logical		etc3
And after this step installing Ubuntu from both Alternate and Desktop disk but both get me stuck as mentioned above.
I also tried deleting all etc3 partitions (so I have a 48.5 GB Free Space) and installing Ubuntu Desktop by restarting the system with the disk in the DVD player.
All do not give a working installation of Ubuntu and bring me to the status that the system stops after Starting Kernel log ... with a black screen. 

Regards, Robert

---

### Post by acefreely on 2006-09-22
Did you get any Grub errors during the Ubuntu install?  

If not boot from the live cd, mount your / partition.  Look at your /boot/grub/menu.lst file and make sure that it is set up correctly.

Also make sure that your / partition is flagged as bootable.

---

### Post by Bunro on 2006-09-22
I had no Grub error.
Could you explain howto or where I can find the steps to mount the disk and what steps to take after.

Regards, Robert

---

### Post by acefreely on 2006-09-22
> **Bunro said:**
> I had no Grub error.
Could you explain howto or where I can find the steps to mount the disk and what steps to take after.

Regards, Robert

You'll need to know the /dev location of your / partition (IE: /dev/sda3).  Then just create a mount point...
```

mkdir /mnt/tmp
```

Then mount your drive...
```

mount /dev/sda3 /mnt/tmp
```

Ubuntu is so cool you'll find that it might do this for you.  I am not sure about that as I just switched from Red Hat last week.

Before you check that though do a ...
```

fdisk -l /dev/sda
```

Where (/dev/sda is the designation for your hard drive) and look for a * next the the partition that is mounted as /.  This indicates that the partition is bootable.

---

### Post by Bunro on 2006-09-22
Thanks every body for the help!
I finally reinstalled every thing again and also installed the ATI driver. This stupid driver is bugging me all the time!
For the moment the system is running again.

Regards, Robert

---

