---
title: "CUPS-missing-filter"
date: 2008-08-15
forum: x86 64-bit Users
---

### Post by NeilBlanchard on 2008-08-15
Hi y'all,

I have a Samsung CLP300 printer on a D-Link network server, and it has worked in the past with x86 64bit, and it currently works with 32bit Ubuntu.  At the moment, I am getting a printer icon on the right side of the Application Places System bar; that says:

Printer 'SamsungCLP-300': cups-missing-filter'.

How can I fix this, and get my printer to work again?

---

### Post by NeilBlanchard on 2008-08-28
Hello,

Bumping my question -- is there a solution for this problem?  It worked in earlier version of 64bit Ubuntu, but it has not worked since I installed HH.

---

### Post by NeilBlanchard on 2008-09-14
Hi,

I sure would like to be able to print again -- does anybody have any hints on how to fix this, please?

---

### Post by NeilBlanchard on 2008-11-07
Bumpity bump.  I'm still hoping to get this fixed!

---

### Post by conehead77 on 2008-11-09
I bump this too, got the same error with my samsung ml-1610. Worked in hardy, now i get this error in intrepid.

---

### Post by jimwhitend on 2008-11-10
Same here with my Samsung ML-1740.  Worked in Hardy, broke in Intrepid.

The suggested fix:

sudo aa-complain cupsd

did not work for me.

Jim

---

### Post by NeilBlanchard on 2008-11-10
Hiya,

I tried what you suggest and I get:

> Setting /etc/apparmor.d/usr.sbin.cupsd to complain mode.


It sounds like it may force the system to "complain" that there is a problem, but not that it is supposed to solve the issue?

---

### Post by lykeion on 2008-11-11
> **conehead77 said:**
> I bump this too, got the same error with my samsung ml-1610. Worked in hardy, now i get this error in intrepid.

Had the same problem. Got it working simply by reinstalling the printer in System > Administration > Printing

Not sure if this is working for 64-bit users (since I'm 32-bit myself).

---

### Post by stormtrooprdave on 2008-11-11
I had the same problem since I upgraded to 8.10 and the solution for me was easy peasy.

Go to System > Administration > Printing
Double click your printer
Go to Policies
Tick enable and apply

My printer began printing again after this, however I just realised that this was disabled again since my last reboot.  I don't know why it doesn't stay enabled between reboots.

---

### Post by NeilBlanchard on 2008-11-11
Hi,

I'd already tried that several times -- I just tried it again, and still no go.

---

### Post by jimwhitend on 2008-11-11
I fixed the problem by installing a new printer and using the recommended driver, which is apparently different than the one that was installed.  This fix sounds easier than it was, however, because browsing to the printer (connected to my Vista box) did not work (for no apparent reason) so I had to key in the the name of the SMB printer.

Now I can print again in all apps except Thunderbird.

---

### Post by NeilBlanchard on 2008-11-13
Hi,

I just decided to try one more time to reinstall the printer, with one of the two recommended drivers -- and this time it worked!

The one that worked is the Samsung CLP-300 Foomatic/foo2qpdl (recommended).  The other one that did not work is Samsung CLP-300 Series (SPL-C) [en] (recommenened).

I don't know why it worked now, and not the other umpteen times I tried -- maybe a recent system update?

---

### Post by conehead77 on 2008-11-14
Reinstalling worked for me too now.

---

### Post by netimen on 2008-12-06
How do I reinstall the printer in kubuntu?

---

### Post by ciamele on 2009-11-10
> **jimwhitend said:**
> Same here with my Samsung ML-1740.  Worked in Hardy, broke in Intrepid.

The suggested fix:

sudo aa-complain cupsd

did not work for me.

Jim

I deleted the printer, rebooted, and Ubuntu reinstalled it for me. That did the trick (with the same model printer).

---

