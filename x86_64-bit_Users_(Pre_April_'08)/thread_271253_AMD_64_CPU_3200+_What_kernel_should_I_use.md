---
title: "AMD 64 CPU 3200+ What kernel should I use???"
date: 2006-10-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by HAL90000 on 2006-10-04
I have a AMD 64 CPU 3200+ - LanParty NF4 Mobo-1 Gig ram - geforce 6600GT 256megs ram

Just wondering which kernel/library should I install?

Thanks 4 your help

---

### Post by Kilz on 2006-10-04
> **HAL90000 said:**
> I have a AMD 64 CPU 3200+ - LanParty NF4 Mobo-1 Gig ram - geforce 6600GT 256megs ram

Just wondering which kernel/library should I install?

Thanks 4 your help

The generic will run, K8 should. You can test it to see if it offers any improvement. Just dont uninstall the generic. If the K8 isnt right all you have to do is boot into the generic in grub.

---

### Post by tseliot on 2006-10-04
linux-k7 for Ubuntu 32bit
linux-k8 for Ubuntu 64bit

---

### Post by HAL90000 on 2006-10-04
One more stupid question...
How can I tell which ubuntu I have 32 or 64?
BTW ..
Im impressed with how rapid your response was...
Thanx

---

### Post by xstaticxgpx on 2006-10-04
> **HAL90000 said:**
> One more stupid question...
How can I tell which ubuntu I have 32 or 64?
BTW ..
Im impressed with how rapid your response was...
Thanx

uname -r in terminal should say i386/amd64/etc

---

### Post by hecato on 2006-10-04
> 
 Just dont uninstall the generic

And how you do that?... isnt the default behaviour? to put the new and backup the old and put them in the grub list?

---

### Post by Kilz on 2006-10-04
> **HAL90000 said:**
> One more stupid question...
How can I tell which ubuntu I have 32 or 64?
BTW ..
Im impressed with how rapid your response was...
Thanx
What version of Ubuntu did you install? The amd64(64bit) or i386(32bit) Since you are in the 64bit section most likely you installed the 64bit version.

> **hecato said:**
> And how you do that?... isnt the default behaviour? to put the new and backup the old and put them in the grub list?

No you can have more than one kernel installed. They get added to your grub list. Its just some people like to keep only a few things and uninstall things before thinking about it.

---

### Post by HAL90000 on 2006-10-04
uname -r in terminal spewed out only "2.6.15-27-386"

---

### Post by xstaticxgpx on 2006-10-04
> **HAL90000 said:**
> uname -r in terminal spewed out only "2.6.15-27-386"
that means you have the 32bit ubuntu installed, use the linux-k7 kernel.

---

### Post by HAL90000 on 2006-10-04
I just got it ALL working (Kubuntu) that is ...
Will installing a new kernel be like resetting everything?

---

### Post by xstaticxgpx on 2006-10-04
> **HAL90000 said:**
> I just got it ALL working (Kubuntu) that is ...
Will installing a new kernel be like resetting everything?

no, none of your files/settings get deleted

---

### Post by HAL90000 on 2006-10-04
kernel amd k7 32 bit Installed fine thanx...
I have been a winders user since dos 3 and Im a lil leary bout extensive system changes ...
Sell ur microsoft stock!

---

