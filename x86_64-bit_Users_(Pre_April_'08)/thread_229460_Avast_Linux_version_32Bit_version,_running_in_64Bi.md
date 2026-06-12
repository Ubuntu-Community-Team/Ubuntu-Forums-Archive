---
title: "Avast Linux version 32Bit version, running in 64Bit"
date: 2006-08-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ausus on 2006-08-04
Hi All,

Has anybody tried to install the Avast 32Bit into 64Bit.
It complains when I try to install.
I have seen that you can force it to run in 32bit mode.
But I cant remember the commands.
Will it then run under 64Bit version.

Regards

---

### Post by Kilz on 2006-08-04
Why would someone what to install antivirus in Ubuntu?
But if its a .deb file you can use
```
sudo dpkg --force-architecture -i PackageName.deb
```

---

### Post by Ausus on 2006-08-04
Hi Kilz,

It is free for home users.
The Package is as follow:avast4workstation_1.0.6-2_i386.deb

Code:
[HTML]sudo dpkg --force-architecture -i avast4workstation_1.0.6-2_i386.deb.deb[/HTML]

Is it this what you hade in mind.


Regards

---

### Post by Kilz on 2006-08-04
> **Ausus said:**
> Hi Kilz,

It is free for home users.
The Package is as follow:avast4workstation_1.0.6-2_i386.deb

Code:
[HTML]sudo dpkg --force-architecture -i avast4workstation_1.0.6-2_i386.deb.deb[/HTML]

Is it this what you hade in mind.


Regards

```
sudo dpkg --force-architecture -i avast4workstation_1.0.6-2_i386.deb 
```
Should do it.  :D 
But, antivirus isnt nessasary on Ubuntu or most Linux distro's. Its a waste of space and processor power. The number of virus threats to Linux can be counted on one hand and require the person to do something stupid, like run as root.](*,)  But if you really want to install it go ahead.

---

