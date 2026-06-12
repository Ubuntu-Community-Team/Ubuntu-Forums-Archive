---
title: "Cupsys troubles"
date: 2005-10-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by postb99 on 2005-10-23
Hi,

I was trying a Breezy Badger AMD64 live CD before I installed it, or not.

Until I understand what's wrong with cupsys running under 64 bits I will get stuck to 32 bits, alas (but will upgrade to Breezy anyway though).

I own a HP Deskjet 710C printer.

Here is the log of /var/log/cups/error_log. However I really wonder what's wrong :-(

What about the error message about no classes defined ? Is this really what makes the test page printing fail ?

I [23/Oct/2005:15:39:15 +0000] Scheduler shutting down normally.
I [23/Oct/2005:15:39:15 +0000] Listening to 7f000001:631
I [23/Oct/2005:15:39:15 +0000] Loaded configuration file "/etc/cups/cupsd.conf"
I [23/Oct/2005:15:39:15 +0000] Configured for up to 100 clients.
I [23/Oct/2005:15:39:15 +0000] Allowing up to 100 client connections per host.
I [23/Oct/2005:15:39:15 +0000] Full reload is required.
E [23/Oct/2005:15:39:15 +0000] LoadAllClasses: Unable to open /etc/cups/classes.conf - No such file or directory
I [23/Oct/2005:15:39:15 +0000] LoadPPDs: Read "/etc/cups/ppds.dat", 4104 PPDs...
I [23/Oct/2005:15:39:16 +0000] LoadPPDs: No new or changed PPDs...
I [23/Oct/2005:15:39:16 +0000] Full reload complete.
I [23/Oct/2005:15:39:25 +0000] Adding start banner page "none" to job 4.
I [23/Oct/2005:15:39:25 +0000] Adding end banner page "none" to job 4.
I [23/Oct/2005:15:39:25 +0000] Job 4 queued on 'DeskJet-710C' by 'ubuntu'.
I [23/Oct/2005:15:39:25 +0000] Started filter /usr/lib/cups/filter/pstops (PID 8119) for job 4.
I [23/Oct/2005:15:39:25 +0000] Started filter /usr/lib/cups/filter/foomatic-rip (PID 8120) for job 4.
I [23/Oct/2005:15:39:25 +0000] Started backend /usr/lib/cups/backend/parallel (PID 8121) for job 4.
I [23/Oct/2005:15:40:26 +0000] Scheduler shutting down normally.
I [23/Oct/2005:15:40:26 +0000] Listening to 7f000001:631
I [23/Oct/2005:15:40:26 +0000] Loaded configuration file "/etc/cups/cupsd.conf"
I [23/Oct/2005:15:40:26 +0000] Configured for up to 100 clients.
I [23/Oct/2005:15:40:26 +0000] Allowing up to 100 client connections per host.
I [23/Oct/2005:15:40:26 +0000] Full reload is required.
I [23/Oct/2005:15:40:26 +0000] LoadPPDs: Read "/etc/cups/ppds.dat", 4104 PPDs...
I [23/Oct/2005:15:40:26 +0000] LoadPPDs: No new or changed PPDs...
I [23/Oct/2005:15:40:26 +0000] Full reload complete.
I [23/Oct/2005:15:40:38 +0000] Adding start banner page "none" to job 5.
I [23/Oct/2005:15:40:38 +0000] Adding end banner page "none" to job 5.
I [23/Oct/2005:15:40:38 +0000] Job 5 queued on 'DeskJet-710C' by 'ubuntu'.
I [23/Oct/2005:15:40:38 +0000] Started filter /usr/lib/cups/filter/pstops (PID 8252) for job 5.
I [23/Oct/2005:15:40:38 +0000] Started filter /usr/lib/cups/filter/foomatic-rip (PID 8253) for job 5.
I [23/Oct/2005:15:40:38 +0000] Started backend /usr/lib/cups/backend/parallel (PID 8254) for job 5.

---

### Post by queenorych on 2005-10-24
I don't see an error here. Increase the verbose level of cups.  I think you have to add -v somewhere in /etc/defaults.  See the man page for cups or cupsys

---

