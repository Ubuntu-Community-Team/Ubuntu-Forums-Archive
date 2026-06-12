---
title: "Has anyone got the Nvidia driver working in 11b?"
date: 2008-04-25
forum: openSUSE and SUSE Linux Enterprise
---

### Post by Growbag on 2008-04-25
I can't seem to find it :(.

Also I'm tried to compile the driver from Nvidia, but can't seem to find the kernel headers.

Uname -r tells me I have version 2.6.25-rc9-17-pae of the kernel running, and Yast tells me I have kernel headers version 2.6.24-18-noarch installed, but then under "File List" there are no files!

Very odd :-k

Oops, sorry, just noticed that there is another thread along the same lines!

---

### Post by Growbag on 2008-05-07
Hah, got it fixed.

I removed the -pae kernel and switched to the standard one.

The driver compiled and installed perfectly after that.

---

### Post by ubuntozack on 2008-05-08
> **Growbag said:**
> I can't seem to find it :(.

Also I'm tried to compile the driver from Nvidia, but can't seem to find the kernel headers.

Uname -r tells me I have version 2.6.25-rc9-17-pae of the kernel running, and Yast tells me I have kernel headers version 2.6.24-18-noarch installed, but then under "File List" there are no files!

Very odd :-k

Oops, sorry, just noticed that there is another thread along the same lines!

um i have been working on it for a couple of weeks havent really seen improvement.

---

### Post by Growbag on 2008-05-10
You have to install it manually using the latest driver from the Nvidia site.

Search for ***kernel*** in Yast2 - Software, and select the ****-pae*** kernel for removal, then select the ***kernel-default*** (from memory) for installation.

Next search for ***linux-*** and select ***linux-kernel-headers*** for installation.

Lastly switch search mode to ***Patterns*** and in the ***Development*** section select ***Base Development*** (you need this for compiling).

Install that lot, reboot, drop to a VT and kill X, then run the Nvidia installer as usual.

---

