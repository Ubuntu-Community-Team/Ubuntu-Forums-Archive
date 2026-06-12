---
title: "Trouble installing 32-bit libs on AMD64"
date: 2007-08-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Atomsk_72 on 2007-08-15
Ok so I just reinstalled Ubuntu (I decided to make the full transition to Ubuntu from Windows). Everything goes great but when I go to install wine it refuses to install the 32-bit dependencies. So I go and install them through the terminal and this is what I get:

> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  lib32asound2: Depends: libc6-i386 (>= 2.5-0ubuntu1) but it is not going to be installed
E: Broken packages

'sudo apt-get install lib32asound2' is the command I used. This happens any time I try to install 32-bit libs I've tried ia32-libs and it still fails with the same message. I've heard that it has something to do with NVIDIA drivers (I'm using 100.14.11) so I uninstall and reinstall as suggested still nothing (I've even tried previous driver versions).

Help please, Thanks.

---

### Post by Kilz on 2007-08-15
> **Atomsk_72 said:**
> Ok so I just reinstalled Ubuntu (I decided to make the full transition to Ubuntu from Windows). Everything goes great but when I go to install wine it refuses to install the 32-bit dependencies. So I go and install them through the terminal and this is what I get:



'sudo apt-get install lib32asound2' is the command I used. This happens any time I try to install 32-bit libs I've tried ia32-libs and it still fails with the same message. I've heard that it has something to do with NVIDIA drivers (I'm using 100.14.11) so I uninstall and reinstall as suggested still nothing (I've even tried previous driver versions).

Help please, Thanks.

try 
```
sudo apt-get clean
```
and 
```
sudo apt-get install -f
```

---

### Post by Atomsk_72 on 2007-08-15
Nope. It still doesn't work.

Thanks for the help.

Edit: Oh um forgot this is the message I got using the previous posts' commands

> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Kilz on 2007-08-15
> **Atomsk_72 said:**
> Nope. It still doesn't work.

Thanks for the help.

Edit: Oh um forgot this is the message I got using the previous posts' commands

Thats possible.

---

### Post by Atomsk_72 on 2007-08-16
Got it fixed it was weird to instead of rebooting after uninstall and install (so thats two reboots) of the NVIDIA drivers I just uninstall, install, start gdm weird stuff.

---

