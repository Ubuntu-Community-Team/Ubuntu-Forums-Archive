---
title: "is there a 64bit moblock for hardy?"
date: 2008-04-30
forum: x86 64-bit Users
---

### Post by gschoppe on 2008-04-30
hi guys,

Is there a repository for a 64 bit Moblock for Hardy?

How would I compile myself?

Is there a natively 64bit alternative?

any other thoughts?

---

### Post by LO Matt on 2008-04-30
[https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)

---

### Post by jamesford on 2008-05-01
just compile yourself, jsut follow the guide here [http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)
its very easy

---

### Post by jre on 2008-05-01
Further I will add amd64 packages support to moblock-deb.sf.net soon. So just add the sources (see links above) now, compile  manually and get surprised when you start getting updates automatically SOON.

---

### Post by ndoggac on 2008-05-21
Successfully compiled the source for Hardy 64 bit.  Used their downloaded script to compile, then installed the deb.  Initially lost all my connections since I was running ssh at the time, and it shut down all my ports...had to plug in the monitor and keyboard temporarily to white list my LAN IP address range, and open up TCP/UDP in port for Azureus.  After restarting moblock (look for the command in the conf file), I was able to access through ssh and webmin successfully.  Thanks for the guide!

---

### Post by jre on 2008-05-22
> **ndoggac said:**
> Successfully compiled the source for Hardy 64 bit.  Used their downloaded script to compile, then installed the deb.
That's no more necessary. Since a few weeks I finally offer amd64 next to i386 packages on moblock-deb.sf.net.

> **ndoggac said:**
> Initially lost all my connections since I was running ssh at the time, and it shut down all my ports...had to plug in the monitor and keyboard temporarily to white list my LAN IP address range
I'm just working on debconf questions for that, so that you will be able to do this during the installation. This will be added in version 0.9~rc2-12.

> **ndoggac said:**
> and open up TCP/UDP in port for Azureus.
Err, are you really sure that you want to do this? Think of the reason that you installed MoBlock!

> **ndoggac said:**
> After restarting moblock (look for the command in the conf file)
Just use "moblock-control restart"

Greets
jre

---

