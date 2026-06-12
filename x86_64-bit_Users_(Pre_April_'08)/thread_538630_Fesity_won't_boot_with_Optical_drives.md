---
title: "Fesity won't boot with Optical drives"
date: 2007-08-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Pde on 2007-08-30
When I upgraded to Feisty, I couldn't get it to boot, so I played around with some stuff and found that if I disconnect my optical drives, it will boot fine.  So now I have Feisty with no optical drives.  The drives are one DVD-RW and one DVD-ROM, on a single IDE connector.  Neither Dapper nor Edgy had this problem.

---

### Post by ddrichardson on 2007-08-31
How are the drives configured master/slave wise and does it happen when the channels are reversed?

---

### Post by Pde on 2007-08-31
Right now the optical drives are on a separate connection than the HDs, the DVD-RW is the master, and the DVD-ROM is the slave.  I don't have time to switch them right now, but I have tried connecting them to a different port on the MB and that doesn't work.  I do know that the HD that Ubuntu is on has to kept in the same configuration that it was installed in, which is slave to my other HD.

---

### Post by ddrichardson on 2007-08-31
Is this purely in respect to the upgrade ot can the Live CD run? Just wondering if there is any commonality is all.

---

### Post by Pde on 2007-09-03
Well at the moment I have it installed, but I did not have the optical drives connected when I installed it.  Could that be the problem?  With my motherboard (ASUS), to install an OS the optical drive and the HD both have to be connected to the same IDE header.  Something about IDE drivers.

---

### Post by ddrichardson on 2007-09-03
Yes that sounds like the problem, are the optical drives specified int /etc/fstab?

---

### Post by Pde on 2007-09-03
The following line from etc/fstab suggests that they are not specified.

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by ddrichardson on 2007-09-03
What happens if you do specify them?

---

### Post by Pde on 2007-09-03
I tried using sudo gedit etc/fstab, but it opened up a blank file.  What am I doing wrong?  And to specify, do I just change the zeros to ones?  Sorry for my newb-ness.

---

### Post by ddrichardson on 2007-09-04
You forgot the leading slash:
```
gksudo /etc/fstab
```

No leave the zero's alone - the ones at the end are to dump and fsck, zero is no and one is yes.

There's a pretty good summary of how fstab operates in the Fedora Core 5 FAQ on my site (in signature).

The command```
fdisk -l
```will show you what is being detected. hda is the primary master on the first IDE channel, is that line the only one or is it the only cd line?

---

### Post by Pde on 2007-09-04
Yeah, after posting that I looked up a tutorial online and figured out how it works.  That's the only line that is mounted on cdrom.  The other lines are floppy, hdb1 and hdb5.  Ubuntu is installed on the slave HD, so I'm guessing  hdb1 is that partition, and hda is my Windows HD.  What is hdb5?

---

### Post by ddrichardson on 2007-09-04
hdb5 would be the 5th partition (assumedly logical), slave on the primary IDE channel.

---

### Post by Pde on 2007-09-04
Following are all the lines in my fstab:

# /dev/hdb1
UUID=dfe6d65e-d219-4675-bc46-6cb95b729ee4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=99f5230b-6c92-4d4b-9e35-0695fe625b24 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0his

Do I need to add a line with /dev/cdrom?  Would it be:

         /dev/cdrom  	   /media/cdrom1  	 auto  	 rw,noauto,user,exec  	  0     0

or something like that?

---

### Post by ddrichardson on 2007-09-04
Yeah that would be correct.

---

