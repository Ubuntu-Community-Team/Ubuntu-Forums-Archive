---
title: "Epson Workforce 500 on 8.10 Printing Endless Blank Paper"
date: 2009-02-06
forum: x86 64-bit Users
---

### Post by slopresto on 2009-02-06
As the subject says, my printer has become a shredder that doesn't shred paper. It works fine when booting into Windows, but under Intrepid it does nothing but continuously feed paper without the heads moving an inch. Canceling the print job does nothing to stop the madness and only after shutting the printer off entirely will the message clear. Cancel is completely unresponsive.

------------------

Dwelling found the actual fix for this issue on both 32 and 64 bit systems. I am editing the post to make it easier to find.

To successfully install the Workforce 500...

1. Remove the Epson Printer if you have already made an attempt to add it.
2. Get the driver packages and install from here: [Download]("http://openprinting.org/show_printer.cgi?recnum=Epson-WorkForce_500")
3. After successfully installing both packages, plug in the printer and it will be auto detected.
4. Run a test page through and it should work just fine.

---

### Post by cariboo on 2009-02-06
It looks like the printer is refusing data, because it needs to be authenticated. Have you checked the cups web interface, to see if you have nneds authentication set? For the cups web interface open Firefox and in the address bar type:

```
http://localhost:631
```

Jim

---

### Post by slopresto on 2009-02-07
Thanks for the tip, although there was no option to remove authentication from the web interface.

The problem is resolved though.

I added the printer from the CUPS web interface and removed the one added through the gnome-cups tool.

Everything worked with no problems at all.

I noticed that the URI from the Web Interface added printer was completely different than the original. I chose the same exact settings for both methods of printer addition and only one works. There must be something wrong with the Printing app in gnome. I had tried removing and readding this printer on multiple occasions.

---

### Post by dwelling on 2009-03-17
Hey.

I just bought the same printer a few days ago and am running Intrepid 32 bit-- exact.  same.  problem.  Same drivers, same issues, everything.

Installing the printer through the CUPS web interface does NOT fix it, however.  I generate different errors in the cups log file (see below.)

Slopresto, could you elaborate on what you did (ie what printer model selected, etc) when installing from the web interface?

I played with the cups configuration to no avail... I think that Cariboo may be on to something, but changing the authentication options present in the file didn't seem to do it.

Any other suggestions?  Thanks for your help.

-dw

driver: Epson E 500 - CUPS+Gutenprint v5.2.0-rc1
cups 1.3.9

Error example:
E [17/Mar/2009:21:42:43 -0600] [Job 34] Unable to write print data: Input/output error
E [17/Mar/2009:21:42:43 -0600] PID 26657 (/usr/lib/cups/backend/hal) stopped with status 1!

---

### Post by OS Freedom Fighter on 2009-03-29
hello all-

I just noticed this thread after posting my own (didn't come up in the pre-search).  I'm running 32-bit also, having the exact same problem.  any new info on the fix?

-MC

---

### Post by dwelling on 2009-03-29
What worked for me was a pretty easy fix.  The gutenprint drivers has two files you must install, and if you only do one (as I had), it will start to recognize the printer, but then pull up a dialog for you to pick the model again.  

Get the driver packages here: [http://openprinting.org/show_printer.cgi?recnum=Epson-WorkForce_500](http://openprinting.org/show_printer.cgi?recnum=Epson-WorkForce_500) 

Be sure to use both debian files.  It's been a few weeks; I'm pretty sure that will do it.  Ubuntu will then recognise your printer no problems, and you can print easily.

---

### Post by slopresto on 2009-04-12
Thanks. I had not done this the first time and it worked, but subsequent attempts had failed. 

I can confirm that installing the x64 packages linked in the previous thread also work for x86_64 systems.

I installed both packages, plugged in the printer and it was immediately detected. I printed a test page and it came out correct on the firs try.

Thanks a bunch.

---

### Post by ricohz on 2009-04-21
hi and thanks in advance for any help i also have same printer,when ever i try to download and install pacages system crashes?

---

### Post by TheMendez1 on 2009-06-07
I had the same problem until I updated the Common UNIX Printing System from the update manager then I downloaded Gutenprint v5.2.0-rc1 then I went to System - Administration - then selected printing from the menu I deleted what said  Epson WorkForce 500 then I plugged in my printer and waited until it said Workforce-500

---

