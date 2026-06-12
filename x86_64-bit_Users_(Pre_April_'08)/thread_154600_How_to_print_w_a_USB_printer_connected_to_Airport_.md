---
title: "?How to print w/ a USB printer connected to Airport Extreme Base Station?"
date: 2006-04-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by davygravy on 2006-04-03
](*,) 

I need to print to an Epson Stylus Color 740 (USB printer) that is attached to an Airport Extreme Base Station. No problems printing to it from our laptops (wirelessly) or from my G4 Tower (running 10.4.5). Just can't get the Ubuntu machine (a B&W G3 upgraded to G4) to see it correctly.

I am running Dapper (was Flight 5, now upgraded to 6), w/ Avahi/Zeroconf installed. The avahi browser shows the ip and ports for the USB printer that is connected to the Airport Extreme, but I cannot print to it. I also have Netatalk installed.

Does the version of CUPS that Ubuntu installs understand APAP (AppleTalk Printer Access Protocol)?

Anyone know how to do this - that is, **anyone actually done it** w/ a USB printer, and willing to post details?

thanks,

davygravy

---

### Post by davygravy on 2006-04-06
I guess this qualifies as a desperate cry for help.

CUPS, my Airport Extreme Base Station and my USB printer aren't actually threatening to hurt me, but I want to avoid hurting them.  Being not prone to violence, I want to try to solve this problem...

I have an established network at home w/ an Airport Extreme Base Station, two wireless Macs running 10.3 & 10.4, a G4 Tower running Tiger & an Epson Stylus Color 740 (USB) attached to the AEBS.  I can print just fine from all three Macs.

My Blue & White G3 is running Dapper Flight 6, and I haven't been able to print to the AEBS-hosted USB printer w/ Linux.

I am familiar w/ CUPS, ipp, etc, but am unable to get the printer to work w/ my Ubuntu/Dapper box.  Anyone out there actually done this (exact) same thing and got it to work?

I've scoured the internet, Apple Dev site, CUPS manual, Linuxprinting.org, everything MacOSXHints, other flavors of Linux (including YDL) but found nothing that works.

Any ideas?

Thanks in advance,

davygravy

---

### Post by goodmaj on 2006-04-23
I am running 5.10.  I have an HP Laserjet 1320 on my airport extreme USB port and print to it as follws:

In Ububtu, Just Pull down System -> Administration -> Printing.
When the Printer box appears, Pull down on "Global Settings" and click on "Detect LAN Printers".  A check mark will appear on the "Detect LAN Printers" next time you look at it.  After a few seconds the Bojour printers will appear.  That is all you should have to do.

If you click on "Detect LAN Printers" for a second time, the Bonjour printers will disappear.

Hope this helps.

---

### Post by goodmaj on 2006-04-23
I am running 5.10.  I have an HP Laserjet 1320 on my airport extreme USB port and print to it as follws:

In Ububtu, Just Pull down System -> Administration -> Printing.
When the Printer box appears, Pull down on "Global Settings" and click on "Detect LAN Printers".  A check mark will appear on the "Detect LAN Printers" next time you look at it.  After a few seconds the Bojour printers will appear.  That is all you should have to do.

If you click on "Detect LAN Printers" for a second time, the Bonjour printers will disappear.

Hope this helps.

---

### Post by davygravy on 2006-04-23
Thanks for the reply.  I actually solved the problem a while back.

I found out that different printers required different levels of effort to get to work...

Since mine was an Epson Stylus Color 740, I found that I had to use HPJetDirect printing (the socket:// protocol).  I also had to back down the firmware on my AEBS to get it to work...

If interested, you can read about it in this ...  [How to Set Up Airport USB Printer]("http://www.ubuntuforums.org/showthread.php?t=156675&highlight=airport+base+station")
It works...though it wasn't easy.

---

