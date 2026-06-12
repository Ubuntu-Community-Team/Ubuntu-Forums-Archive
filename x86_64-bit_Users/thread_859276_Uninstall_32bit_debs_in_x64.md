---
title: "Uninstall 32bit debs in x64?"
date: 2008-07-14
forum: x86 64-bit Users
---

### Post by xinix on 2008-07-14
How do you uninstall 32bit debs installed on a 64bit system?  Is it possible to get some sort of list of what 32bits debs have been installed?

Thanks

---

### Post by Kilz on 2008-07-14
> **xinix said:**
> How do you uninstall 32bit debs installed on a 64bit system?  Is it possible to get some sort of list of what 32bits debs have been installed?

Thanks

[The Search is our friend. ]("http://ubuntuforums.org/showthread.php?t=823150")

---

### Post by xinix on 2008-07-14
Actually I did search for an answer.  But I didn't find anything.  Unfortunately the thread you linked to does not provide any way to get a list of the 32bit debs installed. Nor any suggestion of how to uninstall a 32bit deb, even if you know which one you want to remove.

---

### Post by Kilz on 2008-07-14
> **xinix said:**
> Actually I did search for an answer.  But I didn't find anything.  Unfortunately the thread you linked to does not provide any way to get a list of the 32bit debs installed. Nor any suggestion of how to uninstall a 32bit deb, even if you know which one you want to remove.

Yes it does. [The second post]("http://ubuntuforums.org/showpost.php?p=5148074&postcount=2") in that thread gives details on how to pull up a list of all 32bit debs that are installed on your system.  But since you have to install 32bit debs yourself, you should already know what is installed. 
Once you have the names of the packages there are multiple ways of uninstalling them. Synaptic, apt, dpkg, they will all uninstall packages.

---

### Post by xinix on 2008-07-15
If you want I can post the results from that command, but I can tell you it's not a list of the packages that were installed using the force architecture option with apt. And yes, I know that further down that thread there is another suggested command, but this mainly gave me a list of *.dll file that were in the wine directory.

Unfortunately I cannot get the 32bit debs that I installed to show in Synaptic or to be removed with an 'apt-get remove appname'.

---

