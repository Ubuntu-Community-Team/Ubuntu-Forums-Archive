---
title: "Sys logs growing up to 2GB and killing the OS"
date: 2007-06-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by IFailAtLinux on 2007-06-06
I have kept my PC turned on for 9 days and my syslog and kern.log grew to 1GB each, even though I have that cron job that should keep my logs small. Last date when it worked was yesterday, so 1GB for each log in 1 day is _alot_.

Anyway, my hard disk isn't god-knows-how-big and I realized that something was wrong when in less than 40 minutes my free space there went from 600 megs to 200, before I realized my logs were that big I had 10 megs left, then while asking for help how to fix things I got to 0bytes free on partition mounting to "/" and before I knew that my sytem froze.

Ouch.

I couldn't start X(and anything that wanted to write anything on disk) without root account before I deleted syslog and kern.log(actually I managed to keep kern.log BUT it appears to be 1GB of EMPTY file, probably because I tried to gzip it first... maybe).

But other than that I lost some important data plus many of my software configuration, actually everything that tried to update it's data when things went to 0bytes lost data T_T I lost some important stuff from my apache server as well :/

I don't want that to happen again, so what can I do to limit syslog and kern.log sizes to, well, smaller sizes...  Logs are useful, but mostly the recent ones. Ask whatever you need to know to be able to help, but give me commands I should run to get that info...

---

### Post by jrocket on 2007-06-06
I'm not sure what scripts you could run to keep them at a manageable size, but the first thing that I would do (and what I do on my own server) is to create a partition just for /var.  Give it a couple gigs, that way you can have your logs, but if they get out of hand and fill up the partition it won't affect the rest of the system.

---

### Post by Jouke74 on 2007-06-07
It might also be wise to see what is causing so  many entries and try to solve the problem, or stop logging the issue if it is not important....

---

### Post by Mr. C. on 2007-06-07
If your system logs are growing to over a gig in 9 days, there is something very wrong.

You need to examine the large log files and read them.   What is going on ?

Disabling logging, or just ignoring the output is tantamount to burying your head in the sand to avoid the waves.

Report back what you find.
MrC

---

