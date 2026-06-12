---
title: "Canon LIDE 20 scanner"
date: 2005-02-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by brendand on 2005-02-04
Gentlepeople,

I have just bought the above scanner.  Theoretically it works well in Linux (according to the Sane site) but I am not sure what packages I need to install.  The system recognises the scanner (in Device Manager) but xsane does not.

I think it is because I don't have the correct backend loaded (which according to the Sane site is "plustek") .  Does anyone know how to get a scanner working or a link to a howto for Ubuntu AMD64?

Thanks.

Brendan

---

### Post by kleeman on 2005-02-04
does 'sudo xsane' work? If so it may be a permissions problem. If so execute

sudo chmod a+rw /proc/bus/usb/*/*

and if xsane then finds the scanner put 
chmod a+rw /proc/bus/usb/*/*
in the file
/etc/init.d/local
so the permission problem is solved every boot.

---

### Post by brendand on 2005-02-06
Thanks.  What I did in the end was to add my username to the "scanner" group.

Brendan

---

### Post by stinger30au on 2007-07-28
> **brendand said:**
> Thanks.  What I did in the end was to add my username to the "scanner" group.

Brendan

I hate to sound dumb, but how did you do this.

My LIDE 20 works fine in XP, but in Fiesty i get a black preview and the scanner does not even move an inch!

---

### Post by kleeman on 2007-07-28
Sysem----> Administration-------> Users and Groups

Click on you user name; Click on properties; Click on Users Privileges and check the scanners box

---

### Post by John Jason Jordan on 2007-07-28
> **stinger30au said:**
> My LIDE 20 works fine in XP, but in Fiesty i get a black preview and the scanner does not even move an inch!
Stinger, you may also have been bitten by the USB-suspend bug that was deliberately introduced in the current kernel. I didn't save a link to the thread, but it has been discussed here, along with the workaround. I'm in a hurry or I'd go find the thread. I've posted to it, so search on my name.

---

### Post by viktor.ilijasic on 2007-09-14
Is this the thread you were reffering to?

Link: [Help installing Canon LIDE30 USB scanner](http://ubuntuforums.org/showthread.php?t=497169)

Here is another thread that is close to topic: [ Canon FB630U scanner in x64?](http://ubuntuforums.org/showthread.php?t=446207).

And here is a potential solution: [Fixing a scanner broken by the Feisty upgrade](http://www.ubuntugeek.com/fixing-a-scanner-broken-by-the-feisty-upgrade.html).

I will test if it works properly, and report the results here.

edit: 
It works for me. :D
I haven't noticed CPU usage problems, but I usually disconnect the scanner after scanning, as this computer is a laptop anyhow.

Viktor

---

