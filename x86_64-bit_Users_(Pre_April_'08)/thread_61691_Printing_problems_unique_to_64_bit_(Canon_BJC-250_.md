---
title: "Printing problems unique to 64 bit (Canon BJC-250 (&amp; others ?))"
date: 2005-09-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by phrench_phried on 2005-09-01
I'm something of a noobie and I'm starting to regret either the purchase of the 64 bit processor or not installing the 32  bit Ubuntu on it.  So far, it's been way more trouble than living on the bleeding edge is worth.

There's definitely something wrong with the way Ubuntu 64 handles printing.  I haven't been able to figure out what it is, but I think it must be a problem with CUPS, foomatic, or the drivers.

I have a Canon BJC-250 which has worked with my old compie and every distro of Linux I've tried.  It won't work with my new AMD64 and Ubuntu.  The reason why I say it's a 64-bit related problem is because I can have the printer up and running in about 30 seconds using the Ubuntu x86 live-cd (System -> Admin -> Printing... test page).  I've been reading in this forum and all over the net and it seems like I'm not the only one having this problem or problems a lot like it.  In my particular case, I have the impression that the printer 'thinks' it's printing.  I can see the job go to the print cue and the printer blinks at me for a few minutes then the job leaves the cue and the printer goes back to normal.

Some people report having sporadic printing, others report being able to print from the console using cat <file> > /dev/lp0 or lp <file> but not me, my printer seems to simply quietly digest all print jobs.

Any thoughts from you excellent people?

---

### Post by Corbelius on 2005-09-01
Post the log in /var/log/cups/error_log.

---

### Post by phrench_phried on 2005-09-02
I [02/Sep/2005:09:01:24 +0200] Listening to 7f000001:631
I [02/Sep/2005:09:01:24 +0200] Loaded configuration file "/etc/cups/cupsd.conf"
I [02/Sep/2005:09:01:24 +0200] Configured for up to 100 clients.
I [02/Sep/2005:09:01:24 +0200] Allowing up to 100 client connections per host.
I [02/Sep/2005:09:01:24 +0200] Full reload is required.
I [02/Sep/2005:09:01:24 +0200] LoadPPDs: Read "/etc/cups/ppds.dat", 2350 PPDs...I [02/Sep/2005:09:01:24 +0200] LoadPPDs: No new or changed PPDs...
I [02/Sep/2005:09:01:24 +0200] Full reload complete.
I [02/Sep/2005:09:01:25 +0200] Scheduler shutting down normally.
I [02/Sep/2005:09:01:25 +0200] Listening to 7f000001:631
I [02/Sep/2005:09:01:25 +0200] Loaded configuration file "/etc/cups/cupsd.conf"
I [02/Sep/2005:09:01:25 +0200] Configured for up to 100 clients.
I [02/Sep/2005:09:01:25 +0200] Allowing up to 100 client connections per host.
I [02/Sep/2005:09:01:25 +0200] Full reload is required.
I [02/Sep/2005:09:01:25 +0200] LoadPPDs: Read "/etc/cups/ppds.dat", 2350 PPDs...I [02/Sep/2005:09:01:25 +0200] LoadPPDs: No new or changed PPDs...
I [02/Sep/2005:09:01:25 +0200] Full reload complete.
I [02/Sep/2005:09:04:04 +0200] Adding start banner page "none" to job 8.
I [02/Sep/2005:09:04:04 +0200] Adding end banner page "none" to job 8.
I [02/Sep/2005:09:04:04 +0200] Job 8 queued on 'BJC-250' by 'tom'.
I [02/Sep/2005:09:04:04 +0200] Started filter /usr/lib/cups/filter/texttops (PID 8572) for job 8.
I [02/Sep/2005:09:04:04 +0200] Started filter /usr/lib/cups/filter/pstops (PID 8573) for job 8.
I [02/Sep/2005:09:04:04 +0200] Started filter /usr/lib/cups/filter/pstoraster (PID 8574) for job 8.
I [02/Sep/2005:09:04:04 +0200] Started filter /usr/lib/cups/filter/rastertoprinter (PID 8576) for job 8.
I [02/Sep/2005:09:04:04 +0200] Started backend /usr/lib/cups/backend/parallel (PID 8577) for job 8.

---

