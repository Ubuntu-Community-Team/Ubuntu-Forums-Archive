---
title: "Crossover Office on 64 Bit..."
date: 2009-03-11
forum: x86 64-bit Users
---

### Post by provoked on 2009-03-11
I am having trouble installing this because it fails and tells me that I am missing 32 bit compatibility files. How do I get them?

Edit: Using Ubuntu 8.04 64-bit

---

### Post by cariboo on 2009-03-11
How are you trying to install Crossover? If it is a .deb, just double-click the file and gdebi will take care of the dependency issues for you.

Jim

---

### Post by stchman on 2009-03-11
> **provoked said:**
> I am having trouble installing this because it fails and tells me that I am missing 32 bit compatibility files. How do I get them?

Edit: Using Ubuntu 8.04 64-bit

Do you have the 64 bit .deb file?  If you have the 32 bit .deb file you will need to use the force architecture switch.

---

### Post by provoked on 2009-03-11
The install file I have is a .sh?

---

### Post by justin whitaker on 2009-03-11
> **provoked said:**
> I am having trouble installing this because it fails and tells me that I am missing 32 bit compatibility files. How do I get them?

Edit: Using Ubuntu 8.04 64-bit

You need getlins, which automatically resolves 32bit library dependencies on 64bit systems.

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

Not sure if it works with .sh installer. Why did you pull that one down and not the Ubuntu package, if I may ask?

---

### Post by stchman on 2009-03-11
> **provoked said:**
> The install file I have is a .sh?

I believe Crossover Office is a closed source app based on WINE.  Since you do not have the source you cannot build it.

What Windows app are you wanting to run?  Have you tried WINE?

WINE runs many Windows apps.

---

