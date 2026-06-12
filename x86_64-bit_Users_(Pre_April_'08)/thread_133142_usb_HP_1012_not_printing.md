---
title: "usb HP 1012 not printing"
date: 2006-02-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by oxpack on 2006-02-19
I've been having trouble getting a usb HP 1012 Laserjet working. The hardware is functional since Mozilla and Thunderbird both print. However no KDE apps will print. You will see the item spool in the print manager and then it disappears. I tried the free version of turboprint and it seemed to print. Rather not have to buy it if I can avoid it.

Is there a step by step for diagnosit procedure of CUPS etc anyone can point me to?

Regards-

---

### Post by oxpack on 2006-02-27
FYI 
Turboprint driver seems to print but not perfectly. Page appears shifted down. 
I tried installing hplip-0.9.8 directly from HP with no luck. It compiled but no prints. Still spools but no output.

---

### Post by oxpack on 2006-03-01
Finally - Lord have mercy - got the printer printing. I downloaded a driver from Linux Printing and it worked. Very strange. See below. 

The problem of the "Unsupported Personality: PCL" was finally solved by Carl Michal (michal at physics dot ubc dot ca). By analyzing the output of the Windows driver he found out that after the BeginSession operator in the beginning of a PCL 6 job a special sequence of 8 bytes has to be added. He added it by a filter to the output of GhostScript's "pxlmono" driver and from then on the printer worked.

[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1010](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1010)

Other suggestions I got were to disable the firewall temporarilly while troubleshooting and also trying to print as root to see if it is a permissions problem.

---

