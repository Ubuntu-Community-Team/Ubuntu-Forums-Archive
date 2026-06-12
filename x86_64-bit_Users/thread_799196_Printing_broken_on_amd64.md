---
title: "Printing broken on amd64"
date: 2008-05-18
forum: x86 64-bit Users
---

### Post by Bitch-Face Jones on 2008-05-18
Hi,

I have two printers, a Brother HL-1440 laser printer that is connected to a 32-bit x86 machine (which prints fine) and an HP Photosmart 8450.  I print to the HL-1440 using IPP, and the HP photosmart I guess using some HP protocol to talk to the printer over the network (the device URI shows up as hp:/net/Photosmart_8400_series?ip=192.168.0.103) I'm using the recommended drivers for both of them - foomatic hl1250 for the HL-1440 and foomatic hpijs for the HP.  They both worked fine when I added them, but after a recent update (I'm not sure when, as I use them infrequently) I am unable to print at all.  When I try printing to either one, the job just sits in the printing queue.  Printing to the HL-1440 results in it printing a single page that says the following, no matter what I try to print:

```

-12345X@PJL
@PJL SET MEDIATYPE=REGULAR
-12345X@PJL RESET

```

obviously that isn't very helpful.  This is the entirety of /var/cups/error_log when I try to print:

```
E [18/May/2008:19:21:54 -0500] PID 15870 (/usr/lib/cups/filter/foomatic-rip) stopped with status 1!
E [18/May/2008:19:22:04 -0500] [Job 27] Job stopped due to filter errors.
```

which doesn't really tell me much, either.

When I try removing a job from the printing queue, I get an error that says "There was an error during the CUPS operation: 'client-error-not-possible.'"  Another interesting thing is that printing to a file results in a file that is just a blank page.  I know that Ubuntu isn't quite "there" yet as far as being ready for every day use, but is there any way to correct this?

---

