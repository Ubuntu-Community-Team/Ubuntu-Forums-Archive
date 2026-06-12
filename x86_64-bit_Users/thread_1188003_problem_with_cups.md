---
title: "problem with cups"
date: 2009-06-15
forum: x86 64-bit Users
---

### Post by shayfisher on 2009-06-15
Hello all,

I've installed and configured cups client, but I cannot print.
I've tried to see if there is something in CUPS logs but log directory is empty.
When I try to issue commands like: lpq or lpstat I get error messages,
some are saying Forbidden. Some are saying that there is no default destination.

System info:
2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

Best regards,
shay

---

### Post by chandra on 2009-06-16
There are a couple of cups-related bugs that have been discussed and fixed recently at launchpad. I would suggest that you take a look there.

---

### Post by 4Orbs on 2009-06-16
I had a similar problem recently and finally found a solution on the Crunchbang forum. In the /etc/cups/ssl folder there are two symlinks that point somewhere incorrectly. I disabled those links by renaming them (as root), and the printer worked thereafter. I think there is a more proper fix mentioned on that thread, but I never felt the need to do anything more because I seldom print.

---

### Post by shayfisher on 2009-06-16
Hi there,

Certificates link removal didn't solve anything :(

Chandra... How can I find you specific posts ? I've looked a bit on the launchpad but didn't find anything significant that is similar to my situation.

Thanks.

---

### Post by chandra on 2009-06-19
Take a look at:

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/372166](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/372166)
[https://bugs.launchpad.net/ubuntu/+source/poppler/+bug/382379](https://bugs.launchpad.net/ubuntu/+source/poppler/+bug/382379)

The messages on these bug listings should suggest what you should do.

Another solution is to get the Karmic source package for cups and use prevu to compile it for Jauntu and run it, installing any other necessary packages also from Karmic source. I think I installed two others along the way, but am sorry I cannot recall what they were.

HTH

---

