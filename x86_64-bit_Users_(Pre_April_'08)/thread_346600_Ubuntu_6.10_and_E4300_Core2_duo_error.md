---
title: "Ubuntu 6.10 and E4300 Core2 duo error"
date: 2007-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Rad2 on 2007-01-25
Ubuntu 6.10 and E4300 Core2 duo error.

I have tried everything to get Ubuntu 64 bit to work with my E4300 Core 2 Duo and
the error 152 , You dont have a 64 bit cpu keeps coming up.
Im trying to run it in VMware Server as a Guest OS.
I do have a 64 bit, EM64T cpu can you guys include support for this new cpu in the Duo line of High performing Intel Processors.
[http://www.intel.com/technology/intel64/index.htm](http://www.intel.com/technology/intel64/index.htm)

Xp pro
1 Gig ram
Asrock 775DualVSTA bios 2.40
E4300 Core 2 Duo.

Thank You for your time.

---

### Post by incubus on 2007-01-25
Rad2,

I'm ignorant about what's going on in the hardware world.  But I myself have a core 2 duo and I've been running the 64bit version of Ubuntu for many months.  Never had any problem.

It's really strange that 64bit wont' work.  Have you tried searching the forums for similar problems?  Or google? 

incubus

---

### Post by Rad2 on 2007-01-26
I checked the web and many sites with no help.
I did see some others with similiar posts they cant install because it says
this cpu isnt 64 bit.

---

### Post by accensi on 2007-01-28
If I understood well, you are trying to run Ubuntu 6.10 64 bit version as a guest in Vmware Server. According to Vmware Servewr page, Ubuntu 6.10 64 bit is NOT supported as a guest in Vmware Server release 1.1 and below:

Key Features in VMware Server

What's New in Version 1.0.1

Version 1.0.1 is a maintenance release of VMware Server. It incorporates the following key change:

Performance Improvements on Intel EM64T CPUs
Virtual machines on 64-bit Windows host computers with Intel EM64T CPUs show significant performance improvements.

What's New in Version 1.0

VMware Server 1.0 is a free virtualization product for Microsoft Windows and Linux servers that enables you to provision new server capacity by partitioning a physical server into multiple virtual machines.

VMware Server 1.0 includes:

Support for 32-bit and 64-bit Operating Systems

    * Full support for SUSE Linux 10.1 as host and guest operating systems.
    * Full support for 32-bit Ubuntu 6.x as host and guest operating systems.
    * Full support for 32-bit Sun Solaris 10.x as guest operating systems.
    * Full support for 32-bit and 64-bit FreeBSD 6.0 as guest operating systems.
    * Experimental support for Red Hat Enterprise Linux 3.0 Update 8 and Red Hat Enterprise Linux 4.0 Update 4.
    * Experimental support for 64-bit Ubuntu 6.x as host and guest operating systems.
    * Experimental support for 64-bit Sun Solaris 10.x as guest operating systems.
    * Support for all guest operating systems supported by Workstation 5.5.
    * Support for all host operating systems supported by VMware Server GSX 3.2.

Try to run the 32 bit version!

---

