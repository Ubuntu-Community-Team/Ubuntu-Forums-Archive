---
title: "scanner stopped working after 08.04 upgrade"
date: 2008-11-19
forum: x86 64-bit Users
---

### Post by dmikulec on 2008-11-19
XSANE no longer works with my CanoScan N1220U since upgrading from Gutsy to Hardy. When I launch XSANE a window briefly reports "scanning for devices", then disappears. I've run the following diagnostics:

don@don-desktop:~$ xsane
Segmentation fault


don@don-desktop:~$ groups
don adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev sambashare




don@don-desktop:~$ sane-find-scanner
# sane-find-scanner will now attempt to detect your scanner. If the
# result is different from what you expected, first make sure your
# scanner is powered up and properly connected to your computer.

# No SCSI scanners found. If you expected something different, make sure that
# you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a9 [Canon], product=0x2207 [CanoScan], chip=LM9832/3) at libusb:001:002
# Your USB scanner was (probably) detected. It may or may not be supported by
# SANE. Try scanimage -L and read the backend's manpage.

# Not checking for parallel port scanners.

# Most Scanners connected to the parallel port or other proprietary ports
# can't be detected by this program.

# You may want to run this program as root to find all devices. Once you
# found the scanner devices, be sure to adjust access permissions as
# necessary.


don@don-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 04e8:326c Samsung Electronics Co., Ltd
Bus 001 Device 003: ID 046d:c025 Logitech, Inc. MX500 Optical Mouse
Bus 001 Device 002: ID 04a9:2207 Canon, Inc. CanoScan 1220U
Bus 001 Device 001: ID 0000:0000


don@don-desktop:~$ scanimage -L
Segmentation fault


Seems that the system recognizes the scanner but xsane does not.
I've uninstalled xsane, removed the ~/.sane dir, and reinstalled xsane.

When I launch xsane, these messages appear in syslog:

Nov 16 13:22:15 don-desktop rmmod: ERROR: Removing 'lp': Operation not permitted
Nov 16 13:22:15 don-desktop rmmod: ERROR: Module parport_pc is in use
Nov 16 13:22:15 don-desktop rmmod: ERROR: Removing 'ppdev': Operation not permitted
Nov 16 13:22:15 don-desktop rmmod: ERROR: Module parport is in use by ppdev,lp,parport_pc
Nov 16 13:22:15 don-desktop kernel: [14042.822741] xsane[21639] general protection eip:b6d9dbf5 esp:bf9b9ad0 error:0


My hardware: AMD Athalon64 3400+, 2GB RAM, MAXTOR 6L060J3, 6L060J3 NVIDIA 6L060J3


Thanks, Don

---

### Post by PlaHPoy on 2008-11-19
hrmmm odd problem, hmmmmmm maybe hmmmmm.

---

### Post by dmikulec on 2008-11-30
When I try to run XSane, these messages are recorded in /var/log/syslog:

Nov 30 22:35:30 don-desktop rmmod: ERROR: Removing 'lp': Operation not permitted 
Nov 30 22:35:30 don-desktop rmmod: ERROR: Module parport_pc is in use 
Nov 30 22:35:30 don-desktop rmmod: ERROR: Removing 'ppdev': Operation not permitted 
Nov 30 22:35:30 don-desktop rmmod: ERROR: Module parport is in use by ppdev,lp,parport_pc 
Nov 30 22:35:30 don-desktop kernel: [ 7446.095426] xsane[6276] general protection eip:b6de8bf5 esp:bfd46b20 error:0

Regards,

Don

---

### Post by Sef on 2008-12-01
Download the Live CD and see if you have the same problems or not.

---

### Post by dmikulec on 2008-12-01
I've just tried "sudo xsane" and it worked. I'm thinking there's a permissions problem somewhere but don't know how to uncover it.

TIA,

Don

---

### Post by sanitycheck on 2008-12-15
Kubuntu upgrade from Gutsy 7.10 to Hardy 8.04.  I observe the same problem with a Canon CanoScan N670U.  It worked in 7.10.  Now I select it from the list when XSane starts, but XSane never actually runs.  

The scanner does work when selected in Kooka, however.

I do see this in syslog:

```
Dec 15 14:30:55 california kernel: [229464.899879] xsane[6988]: segfault at 00000010 eip 080c3179 esp bf942470 error 4
Dec 15 14:31:17 california kernel: [229487.387093] xsane[7015]: segfault at 00000010 eip 080c3179 esp bfe8a040 error 4
Dec 15 14:31:43 california kernel: [229512.999724] xsane[7052]: segfault at 00000010 eip 080c3179 esp bff52100 error 4
```

---

### Post by gypaete09 on 2008-12-23
As opposed to dmikulec I not even upgraded to 8.04 because my machine would then freeze again and again, so I reinstalled 7.10, until I'll have time to do a fresh 8.10 install.

But recently Xsane stopped working with my HP3055 multifunction printer over ethernet.
The window "scanning for devices" initially used to find the webcam and the scanner/printer, then lately stopped fining the webcam (good .. it would not ask me to choose anymore), but now it doesn't find anything and the window disappears, Xsane does not run.

I tried the diagnostics listed above and I find a USB device (probably my webcam again :-) and that's it. Ethernet devices may not be found by sane-find-scanner, is what the text output seems to tell me, anyway.

I ran xsane as root, but the result is the same - no device found.

Since I am mad enough to run my daily work under Linux, I would really love to scan again without booting XP "just" for that... 

If anyone knows a way to get xsane to work again (older version?) I'd like to hear from you.


SELF-reply (Edit):

Found the way out.. while fiddling with xsane reinstall, cupsys became unstable and printing became impossible, not only scanning.
As soon as I wanted to change something in System/printing, the CUPSD fell over and became unavailable.
A few cupsd stops and starts still would wake it up, but then it died altogether.
hp-check would only show my webcam.

Finally I did:
deinstall/reinstall xsane (maybe not necessary), but upgraded
Xsane would now start, but show the webcame name as device description - no good, but some progress.
I downloaded and reinstalled HPLIP (newer version), 
... which screamed after CUPS (not cupsys),
I deinstalled/reinstalled cupsys (quite probably unnecessary), because all I needed was
to recreate a link called "cups" pointing to cupsys in /etc/init.d
then I restarted and correctly finished the HPLIP reinstall
After that everything worked fine - scanning AND printing, and I see the webcam again as one of the devices to choose from.. so what.

I use Gutsy (with kernel 2.6.22.14, because it upsets my still necessary Virtualbox with XP)

The download location for HPLIP is here: [http://hplipopensource.com/hplip-web/gethplip.html](http://hplipopensource.com/hplip-web/gethplip.html)
A link to the step by step install instructions is right on that page.

Thanks again to all - without the ubuntuforums the upgrades that break things would be a even bigger pain in the butt.

cheers
Certainly there was an easier way, but often on Linux I am alone, except for some posts that give me hints, not ready-made solutions. Lucky enough, I wasn't the only one who had this regression problem.

Thanks to all you nameless posters.

---

### Post by sanitycheck on 2009-02-01
Tired of my scanner (cheap copy machine) not working, I finally found a fix for this problem searching Google yet again.

Delete the (hidden) .sane directory in your home directory.  When you run XSane again, it will recreate the directory.  XSane should now come up when you select your scanner from the list (instead of disappearing).

Clearly something the previous (Gutsy) version put in /.sane made the Hardy version crash.

This meant I had to configure the Copy function again for my network printer, because deleting the .sane directory wiped out the previous (Gutsy) saved settings.

For Kubuntu network printing, look to the XSane documentation [[COLOR="RoyalBlue"]here[/COLOR]]("http://www.xsane.org/doc/sane-xsane-setup-copy-doc.html").

In particular:

> When you use KDE then you should try "kprinter --stdin"

Also, un-checking the "create zlib compressed postscript image..." is still necessary to prevent the disappearing print job problem described [[COLOR="RoyalBlue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?p=4147428&posted=1#post4147428").

---

