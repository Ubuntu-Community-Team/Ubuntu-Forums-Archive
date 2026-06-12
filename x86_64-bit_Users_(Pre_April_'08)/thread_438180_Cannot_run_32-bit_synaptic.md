---
title: "Cannot run 32-bit synaptic"
date: 2007-05-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by shame on 2007-05-09
I followed the guide here to set up a 32-bit chroot on feisty: [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

Mostly it is working well but I am unable to run the 32-bit synaptic properly.
I can check for updates with it and select packages to install or remove it gets as far as downloading the packages but then crashes before actually making any changes.  I get this in the terminal: ```
Internal Error: impossible to fork children. Synaptics is going to stop. Please report.
```

---

### Post by mckryptyk on 2007-05-09
Hi, I have a chroot on feisty for firefox, wine, synaptic and others.

The guide I used is: 
[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

After looking at your link, I believe it is compatible with yours.
You should look at it and see if it can help you.  :)  

When installing a chroot only install the absolute bare minimum. 
No one should have to install 'ubuntu-desktop'.

This will also make it easier to troubleshoot any problems.

*Also a common problem is " mount --bind 'whatever' " not being used correctly.
Although I don't think that is your problem*

Cheers.

---

### Post by shame on 2007-05-10
I managed to get it running without the crashes.
I had to add another line to fstab to bind /dev/pts.  Although /dev is already there for some reason there was nothing in /dev/pts.
It's now running fine.

---

### Post by mckryptyk on 2007-05-10
So it was the "mount --bind" problem! 
Glad to see you got it fixed :)

Cheers.

---

