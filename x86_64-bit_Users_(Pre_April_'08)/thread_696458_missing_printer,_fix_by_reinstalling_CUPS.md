---
title: "missing printer, fix by reinstalling CUPS"
date: 2008-02-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by maphew on 2008-02-14
Hi All,

Twice in the last week my printer has disappeared from the Printer Configuration (system > admin > printing) applet. On the left hand side there is "Server Settings" but no "Local Printers", even the file PDF printer is gone. Rebooting the computer makes no difference. Under the Edit menu 'New Printer' and 'New Class' are disabled.

I managed to get the printer back by using Synaptic Package Manager to reinstall everything that starts with "cupsys" (5 programs, they all showed as being installed already). I'm posting this note here in case someone else is having the same difficulty.If it happens to me again I'll follow up with more details (like which package exactly needs to be reinstalled).

My computer is AMD64 ubuntu 7.10 (upgraded from 7.04).
Linux ubuntu-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux

2008-Feb-24: happened again today, after a reboot. It was sufficient to reinstall only cupsys to get the printer back. Still going to be a pain if I have to do this after every restart. 

Oh, I see I forgot to say what kind of printer: HP Deskjet 932C, connected via USB.

---

