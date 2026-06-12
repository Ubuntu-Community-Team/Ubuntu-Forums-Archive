---
title: "Upgrade to 9.1 issue"
date: 2009-11-05
forum: x86 64-bit Users
---

### Post by belfasttim on 2009-11-05
Hi-- I decided to go ahead and upgrade from 9.04 to 9.1 this afternoon, backed up my files and took the plunge.

I am unable to startup Ubuntu  post-upgrade-- I get a 

Gave up waiting for boot device. Common problems . . . etc.

Then: 

ALERT! /dev/sda2 does not exist. Dropping to a shell.

When I boot from a live CD, it appears the upgrade, rather than upgrading my 9.04 that lived on sda1, created a new partition (sda2) and installed 9.1 there. It looks like the whole filesystem on sda1 is intact.

But booting from grub apparently it can't find sda2, and when I edit the boot statement to try to boot from sda1 I get the same results.

Any help, please?

---

### Post by belfasttim on 2009-11-05
Update--

it appears for some reason my system was not recognizing the primary HD, so I disconnected the second HD and it booted almost properly (at least, this time it found sda2 so it continued the boot).

However, as soon as the "starting up" message appeared, it began to blink very rapidly, then dropped into a shell login while coninuing to flash. The keyboard is acting very erratic, so I can't log in, since I assume my password is getting mistyped.

Very strange. Any ideas welcome.

---

### Post by belfasttim on 2009-11-05
Looks like my hardware didn't like the 2.6.31 kernel. I was able to boot into the 2.6.28 without major issue, though cairo  dock is acting pretty odd.

Hope this helps someone.

---

