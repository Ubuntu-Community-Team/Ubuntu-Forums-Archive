---
title: "Linux chipset driver for Asus M4A___ series"
date: 2009-08-06
forum: x86 64-bit Users
---

### Post by Rebelli0us on 2009-08-06
I noticed that the CD for my new Asus AM3 mobo contains Linux chipset driver -- ati-driver-installer-8-7-x86.x86_64.run

Has anybody tried it? Does it even work in Ubuntu 9.04  64?

I noticed that power consumption @ idle in 9.04 is 10-12 watts more than Windows -- CPU driver, chipset or video?

---

### Post by Yellow Pasque on 2009-08-06
It looks like it contains Catalyst/fglrx 8-7, which won't work in Ubuntu 9.04. You need at least Catalyst version 9-4, which should be installable from the System -> Administration -> Hardware Drivers menu.

> I noticed that power consumption @ idle in 9.04 is 10-12 watts more than Windows -- CPU driver, chipset or video?
If you're using an open-source video driver, it's probably the GPU. ATI never released docs on their "Powerplay" GPU undervolting/clocking. The devs are reverse-engineering it, but it's not complete yet, and I think it's only in the very latest code (i.e. you would have to use a PPA like: [https://launchpad.net/~tormodvolden/+archive/ppa](https://launchpad.net/~tormodvolden/+archive/ppa) or checkout the git code and compile the driver yourself)

See: [http://www.phoronix.com/forums/showthread.php?t=16468](http://www.phoronix.com/forums/showthread.php?t=16468)

---

### Post by Rebelli0us on 2009-08-06
Boy you sure know your stuff. Do you have an Asus M4A___ series? The AMD/ATI video driver was a bust for me:

[http://ubuntuforums.org/showthread.php?p=7743650#post7743650](http://ubuntuforums.org/showthread.php?p=7743650#post7743650)

---

