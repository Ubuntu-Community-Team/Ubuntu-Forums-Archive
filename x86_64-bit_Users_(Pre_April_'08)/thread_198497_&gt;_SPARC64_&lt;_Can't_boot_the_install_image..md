---
title: "&gt; SPARC64 &lt; Can't boot the install image."
date: 2006-06-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by chris_andrew on 2006-06-17
Hi,

I've just downloaded the much awaited *sparc64* image, from the mirrors.  Unfortunately, I didn't get far with the Ultra 10 install.  I was pleased to see the *SILO* message, then I chose *install* from the *boot:* prompt, but unfortunately, the install hung at *"Booting Linux"*.  

I checked the Debian Etch latest sparc release notes, for any clues, and attached > ramdisk_size=16000 as a boot option.  Still no luck.

Anybody else had this problem?

Many thanks,

Chris.

(Well done to the Sparc guys, for getting this release out).

---

### Post by termdex on 2006-06-19
I have a similar system: Ultra 10 with Creator3D. I also got the same symptoms.  I figured that maybe the default kernel wasn't configured for that frame buffer so I tried serial console.  I'm no farther along but I did get the following output on serial:

boot:
Allocated 8 Megs of memory at 0x40000000 for kernel
Loaded kernel version 2.6.15
Loading initial ramdisk (4821666 bytes at 0x10400000 phys, 0x40C00000 virt)...
Illegal Instruction

where it goes back to the 'ok' prompt.

---

### Post by netztier on 2006-06-19
[QUOTE=chris_andrew]
Anybody else had this problem?
[/QUOTE]

No luck so far with the hints and suggestions from your [netboot thread]("http://www.ubuntuforums.org/showthread.php?t=185136&highlight=sparc")?

What you basically need (RARP deamon, TFTP Server, [netboot image]("http://ports.ubuntu.com/ubuntu-ports/dists/dapper/main/installer-sparc/current/images/sparc64/netboot/2.6/")) is described in the thread... please give it a try - and/or report success or failure before starting another thread and another...

Did you upgrade the OBP as suggested in this [Bug Report]("https://launchpad.net/distros/ubuntu/+source/silo/+bug/40119")?

kind regards, 

Marc

---

### Post by chris_andrew on 2006-06-19
SILO bug reported.

---

### Post by termdex on 2006-06-19
Upgrading the OBP from 3.25 to 3.31 solved the problem.
Thanks.

---

### Post by chris_andrew on 2006-06-20
termdex,

Upgrading the OBP?  Any idea how i'd do this, I don't have access to Solaris Cd's.

Cheers,

Chris.

---

### Post by chris_andrew on 2006-06-20
Started new thread at:

[http://www.ubuntuforums.org/showthread.php?p=1161695#post1161695](http://www.ubuntuforums.org/showthread.php?p=1161695#post1161695)

Chris.

---

