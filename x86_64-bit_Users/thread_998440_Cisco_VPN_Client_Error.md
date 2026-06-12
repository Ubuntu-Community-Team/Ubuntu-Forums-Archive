---
title: "Cisco VPN Client Error"
date: 2008-11-30
forum: x86 64-bit Users
---

### Post by nkingcade on 2008-11-30
When I try to connect to my network using the Cisco client in this version, I get a "segmentation fault". To me that means I am trying to write to a memory area and that's not allowed here. Has anyone else seen this problem? Is there a fix? Thanks in advance.

---

### Post by midnightflash on 2008-12-04
Yes... having the same problem on my new machine. With both systems: Intrepid 64bit AND Gentoo 32bit.

Even worse... the virtual machine (a Debian stable 32bit, just builded for the VPN-tunneling, that was working on the old Athlon-XP machine) has the same error now too from within both host-systems.

Very strange and confusing! :???:

Seems to be a problem with the (Phenom-)processor, the ATI 780 chipset or something. :roll:

---

### Post by nkingcade on 2008-12-04
I have a ticket open on this with Cisco TAC since it is related to my ability to work from home. I will let you know what I find out from them. They have already assigned an engineer and he has contacted me and requested screenshots of the problem and make an model of the distro. I'll get back to you when I have a solution.

Neal

---

### Post by midnightflash on 2008-12-05
That's nice to know.

If they need more informations... I'm also very willing to give them too.
(Needing it for work too also btw...)

---

### Post by nkingcade on 2008-12-05
Flash,

Sorry to be the bearer of bad news. Cisco got back to me. The bottom line is that the client uses 32bit libraries and not 64 bit. Cisco will not support any 64 bit kernels. I am going to continue to look into this issue. I know someone has beat this horse. If I find anything, I'll let you know

Neal

---

### Post by dcstar on 2008-12-07
And I assume everyone has read this:

[http://ubuntuforums.org/showthread.php?t=765975](http://ubuntuforums.org/showthread.php?t=765975)

---

### Post by nkingcade on 2008-12-07
No, I had not read this procedure. However, I will uninstall what I have and reinstall and patch. Details at eleven with film.

Neal

---

### Post by bp1509 on 2008-12-07
d

---

### Post by killer2239 on 2008-12-07
Not sure if this info is of any help. But iv researched 64-bit cisco vpn issues a month or 2 ago. They do not even support 64-bit for windows yet with their vpn. If anyone finds a solution to get connected to a cisco vpn network with Linux 64-bit please let me know though. Save me from busting out my laptop when im at home if im oncall.

---

