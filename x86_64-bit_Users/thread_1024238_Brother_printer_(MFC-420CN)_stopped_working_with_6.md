---
title: "Brother printer (MFC-420CN) stopped working with 64bit 8.10"
date: 2008-12-28
forum: x86 64-bit Users
---

### Post by cherukan on 2008-12-28
I had this working on i386 using drivers and following instructions from Brother's website.

[http://solutions.brother.com/linux](http://solutions.brother.com/linux)

but this stopped working after I upgraded my hardware and OS to 64bit.

The scanner on the MFC works fine, but the printing does not.
CUPS says that the job has completed, but nothing prints.

How can I diagnose whats going on?

Thanks in advance.


CUPS error log:

D [28/Dec/2008:17:12:29 -0800] Saving remote.cache...
I [28/Dec/2008:17:12:29 -0800] Listening to 127.0.0.1:631 (IPv4)
I [28/Dec/2008:17:12:29 -0800] Listening to /var/run/cups/cups.sock (Domain)
I [28/Dec/2008:17:12:29 -0800] Loaded configuration file "/etc/cups/cupsd.conf"
I [28/Dec/2008:17:12:29 -0800] Using default TempDir of /var/spool/cups/tmp...
I [28/Dec/2008:17:12:29 -0800] Configured for up to 100 clients.
I [28/Dec/2008:17:12:29 -0800] Allowing up to 100 client connections per host.
I [28/Dec/2008:17:12:29 -0800] Using policy "default" as the default!
I [28/Dec/2008:17:12:29 -0800] Partial reload complete.
I [28/Dec/2008:17:12:29 -0800] Listening to 127.0.0.1:631 on fd 2...
I [28/Dec/2008:17:12:29 -0800] Listening to /var/run/cups/cups.sock on fd 4...
I [28/Dec/2008:17:12:29 -0800] Resuming new connection processing...
I [28/Dec/2008:17:12:35 -0800] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=7504)
I [28/Dec/2008:17:12:35 -0800] Started "/usr/lib/cups/cgi-bin/admin.cgi" (pid=7505)
I [28/Dec/2008:17:12:36 -0800] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=7506)
I [28/Dec/2008:17:12:39 -0800] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=7507)
I [28/Dec/2008:17:12:39 -0800] [Job 32] Adding start banner page "none".
I [28/Dec/2008:17:12:39 -0800] Saving subscriptions.conf...
I [28/Dec/2008:17:12:39 -0800] [Job 32] Adding end banner page "none".
I [28/Dec/2008:17:12:39 -0800] [Job 32] File of type application/postscript queued by "zzt".
I [28/Dec/2008:17:12:39 -0800] [Job 32] Queued on "MFC420CN" by "zzt".
I [28/Dec/2008:17:12:39 -0800] Saving subscriptions.conf...
I [28/Dec/2008:17:12:39 -0800] [Job 32] Started filter /usr/lib/cups/filter/pstopdf (PID 7508)
I [28/Dec/2008:17:12:39 -0800] [Job 32] Started filter /usr/lib/cups/filter/pdftopdf (PID 7519)
I [28/Dec/2008:17:12:39 -0800] [Job 32] Started filter /usr/lib/cups/filter/cpdftocps (PID 7534)
I [28/Dec/2008:17:12:40 -0800] [Job 32] Started filter /usr/lib/cups/filter/brlpdwrapperMFC420CN (PID 7535)
I [28/Dec/2008:17:12:40 -0800] [Job 32] Started backend /usr/lib/cups/backend/usb (PID 7539)
I [28/Dec/2008:17:12:40 -0800] Saving subscriptions.conf...
I [28/Dec/2008:17:12:40 -0800] Saving subscriptions.conf...
I [28/Dec/2008:17:12:40 -0800] Saving subscriptions.conf...
I [28/Dec/2008:17:12:41 -0800] Saving subscriptions.conf...
I [28/Dec/2008:17:12:42 -0800] [Job 32] Completed successfully.
I [28/Dec/2008:17:12:42 -0800] Saving subscriptions.conf...
I [28/Dec/2008:17:12:42 -0800] Saving subscriptions.conf...

---

