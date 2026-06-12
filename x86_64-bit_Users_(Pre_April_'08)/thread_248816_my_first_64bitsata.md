---
title: "my first 64bit/sata?"
date: 2006-09-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by takiniteasy on 2006-09-01
I have a AMD running a 400gig hdd-sata. when I boot form the cd I get a message stating [COLOR="Red"]"[160.932012] hdc idenity: huh? expected null" [/COLOR] my hdd has no jumper because it is sata I think that is right anyways, and the cd/dvd/rw is no ide but it also has no jumper. is there something wrong with this set up that anyone knows of?

---

### Post by John.Michael.Kane on 2006-09-01
If theres no jumper on the cd/dev drive it could be sata based. is the cable for the dvd/cd drive thin like your sata drive or is it wide?

---

### Post by takiniteasy on 2006-09-01
no it seems to be a reg. ribbon but if you look at the boot screen it shows as a second sata?

---

### Post by takiniteasy on 2006-09-01
sorry I just read my first post. I was supposed to say that the cd/dvd is set up as ide but it does not have a jumper. that is why I thougt there might be a problem when I try to boot the system. I did try to put a second hdd in it using the ide and I set the jumper on that one to master and the bios saw it as master and the sata hdd was 1st sata but suse 10.2 would not find the master hdd so I took it out? I am just new to the sata inviroment. but thanks for the help=D>

---

### Post by John.Michael.Kane on 2006-09-01
Can you check the order of the  or drive in the bios?

Make sure the bios see's the dvd as an ide device.

also is there any markings on the cd drive for mastr slav cableselect?

---

### Post by a-musing amazon on 2006-09-03
Usually (i.e. on my PC!) the SATA drive will report as /dev/sda not as /dev/hd? [? being a number]. Older, PATA drives are seen as /dev/hd? - in other words SATAs are treated as a pseudo-SCSI not as IDE. On my PC this was also the case when I previously used Knoppix as my distro.

They also use have different sorts of ribbon cable/connect which only fit the appropriate SATA connecters/controllers on the motherboard.

Have you had your setup working previously on another linux distro with the SATA HD mapped to /dev/hda3?

On the other hand you could be having a problem with your other hardware if it was jumpered as slave and there is no master installed on the same IDE connection.

---

### Post by mgmiller on 2006-09-03
If the optical drive is PATA, also known as IDE, & uses the old style wide ribbon cable, then it must have jumpers.  Printed on the case sticker, or embossed into the metal of the case will be the clue to tell you which is master, slave or cable select.  Sometimes the embossed labels are hard to see.  They may only be only 1 or 2 letters, like, M S CS.  If there is no jumper installed in any of the positions, this could be causing your problem.  Jumpers are normally installed vertically.

---

