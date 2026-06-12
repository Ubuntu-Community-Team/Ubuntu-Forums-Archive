---
title: "ubuntu 64 (all flavours) will not install"
date: 2007-08-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by whb on 2007-08-31
Regretfully I am writing from a Suse 10.3 64 bit installation which was painful but installed. Fedora 64, Sabayon 64 also install. Ubuntu alternate complains about corrupted files then quits. Ubuntu desktop, LTS through gutsy installs the kernel then ziltch, I am staring at a blank screen forever. I have added all the usual parameters to the boot, noapic etc., to no avail.

My computer has an Asus KFN5-D SLI motherboard, GeForce8800 GTS video driver, an AMD opteron 2202 cpu, and a WD740 hard drive.

I find it strange that all these other flavours of linux install (Fedora was particularly easy) none of which I want, but Ubuntu which I** do** want fails miserably. Does anyone know how to get round this. I suspect it needs some BIOS adjustment.  Thanks for any help,

Hunter

---

### Post by Kilz on 2007-08-31
> **whb said:**
> Regretfully I am writing from a Suse 10.3 64 bit installation which was painful but installed. Fedora 64, Sabayon 64 also install. Ubuntu alternate complains about corrupted files then quits. Ubuntu desktop, LTS through gutsy installs the kernel then ziltch, I am staring at a blank screen forever. I have added all the usual parameters to the boot, noapic etc., to no avail.

My computer has an Asus KFN5-D SLI motherboard, GeForce8800 GTS video driver, an AMD opteron 2202 cpu, and a WD740 hard drive.

I find it strange that all these other flavours of linux install (Fedora was particularly easy) none of which I want, but Ubuntu which I** do** want fails miserably. Does anyone know how to get round this. I suspect it needs some BIOS adjustment.  Thanks for any help,

Hunter

Are you trying the live cd or the (works for me all the time) alternate install cd?

---

### Post by John.Michael.Kane on 2007-08-31
> **whb said:**
> Regretfully I am writing from a Suse 10.3 64 bit installation which was painful but installed. Fedora 64, Sabayon 64 also install. Ubuntu alternate complains about corrupted files then quits. Ubuntu desktop, LTS through gutsy installs the kernel then ziltch, I am staring at a blank screen forever. I have added all the usual parameters to the boot, noapic etc., to no avail.

My computer has an Asus KFN5-D SLI motherboard, GeForce8800 GTS video driver, an AMD opteron 2202 cpu, and a WD740 hard drive.

I find it strange that all these other flavours of linux install (Fedora was particularly easy) none of which I want, but Ubuntu which I** do** want fails miserably. Does anyone know how to get round this. I suspect it needs some BIOS adjustment.  Thanks for any help,

Hunter

Usually when the cd complains about corrupted files that's due to a badly burned cd. Have you tried burning the iso to cd slower,

---

### Post by Jouke74 on 2007-08-31
(Hi Kilz, we are replying too much together :-) )

Is there a Jmicron IDE / SATA controler on your MOBO? Ubuntu does not really like this one if I remember well. You might want to try to move your disk drives to the other controller which should be there. Then try a reinstall. Indeed first check the CD before start. There is an option under the install menu.

---

### Post by whb on 2007-08-31
both live and alternate. One of the gutsy lives actually got to the desktop live, but then would not install,

Hunter

---

### Post by whb on 2007-08-31
burned as slowly as I can,

Hunter

---

### Post by whb on 2007-08-31
I have no idea what kind of controller is there. Some kind of SATA controller. How would I change?

Hunter

---

### Post by Jouke74 on 2007-08-31
Yes that is a sata / ide controller and that would mean opening the computer and move the cables of your disks to the other one. Not that easy, and not advisable if you have not done it before.

---

### Post by whb on 2007-08-31
Thanks for the idea, but the thought of opening this thing and moving cables brings me out in a cold sweat,

Hunter

---

### Post by Jouke74 on 2007-08-31
Hmm  further reading also indicates that with 7.04 the Jmicron problem should be over...

---

### Post by whb on 2007-08-31
Well I am now downloading Feisty 64 alternate and desktop. Maybe getting them and burning them on Suse will bring me a change of fortune. That would be ironic, but I do not care as long as I can get back to Ubuntu,

Hunter

---

### Post by Kilz on 2007-08-31
> **whb said:**
> Well I am now downloading Feisty 64 alternate and desktop. Maybe getting them and burning them on Suse will bring me a change of fortune. That would be ironic, but I do not care as long as I can get back to Ubuntu,

Hunter

Make sure to check the md5sum of the iso before burning it to make sure you get a good file to burn.

---

### Post by whb on 2007-08-31
> **Kilz said:**
> Make sure to check the md5sum of the iso before burning it to make sure you get a good file to burn.

Will do,

Hunter

---

### Post by kuja on 2007-08-31
Oh, and failing this, you could always try the gutsy alternate, if gutsy live got to the desktop then theoretically so long as the install goes smooth (perhaps it would with the alternate) you should be good to go eh?

---

### Post by whb on 2007-08-31
well, the Suse burned ubuntu disks did not work. MD5sum's were good but checking the alternate from the boot menu showed corrupted files - well the kernel was co I quit at that point. The problem seems to be with the burn. I am back in Feisty now, so will try again, maybe with gutsy alternate,

Thanks to everyone for their comments.

Hunter

---

