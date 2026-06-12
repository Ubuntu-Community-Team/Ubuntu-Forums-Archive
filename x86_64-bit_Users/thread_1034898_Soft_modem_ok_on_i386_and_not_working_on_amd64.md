---
title: "Soft modem ok on i386 and not working on amd64"
date: 2009-01-09
forum: x86 64-bit Users
---

### Post by egalua on 2009-01-09
Hi all, 

I have an usb modem which, using lsusb, identifies itself as

Bus 003 Device 002: ID 0483:7554 SGS Thomson Microelectronics 56k SoftModem

I have two desktops one with 8.10/i386 and the other with 8.10/amd64.

On the first the modem works using the package sl-modem-daemon.
On the second, the package is not in the repository.

Is there a way to use the modem on the  64bit desktop?

TIA

Fabio

---

### Post by dadozgb on 2009-01-09
> **egalua said:**
> Hi all, 

I have an usb modem which, using lsusb, identifies itself as

Bus 003 Device 002: ID 0483:7554 SGS Thomson Microelectronics 56k SoftModem

I have two desktops one with 8.10/i386 and the other with 8.10/amd64.

On the first the modem works using the package sl-modem-daemon.
On the second, the package is not in the repository.

Is there a way to use the modem on the  64bit desktop?

TIA

Fabio

Well in theory it sholud work but I never did such thing. You have to download source of that package and compile it for 64 bit arch. To see how can you compile it for 64 bit arch check gcc manual and docs.

---

### Post by egalua on 2009-01-09
> **dadozgb said:**
> Well in theory it sholud work but I never did such thing. You have to download source of that package and compile it for 64 bit arch. To see how can you compile it for 64 bit arch check gcc manual and docs.

I thought this could be a way, but it seems to me that even the source is meant for i386:
[http://packages.ubuntu.com/intrepid/sl-modem-source](http://packages.ubuntu.com/intrepid/sl-modem-source)

Or am I making a big mistake? In this case, it is not clear to me how to compile it.

Thanks

Fabio

---

### Post by phlembob on 2009-01-10
Fabio,
You may need a 32 bit version of Intrepid.  On Hardy you can download the 32 bit libraries so I think you can do it with Intrepid too --- that is the problem you can't download.  Perhaps you may want to install hardy and upgrade Hardy.  Then upgrade again to 8.10.  You can see if this will work.  I don't know I've have gone back to Hardy LTS.  It is more stable.
:guitar:

---

### Post by Thelasko on 2009-01-12
It appears this piece of software is written specifically for i386 architecture.  It interfaces with the kernel so it isn't portable to other architectures without a rewrite.

I was about to recommend that you file a bug report (and still do), when I discovered [this bug]("https://bugs.launchpad.net/ubuntu/+source/sl-modem/+bug/151562").  A hack is posted that tells you how to install a version from Debian that supports amd64.  Debian is very similar to Ubuntu, so it should work fine.  I recommend you comment on this bug and click the "this affects me" button to let the developers know they need to step up support on this.

---

### Post by egalua on 2009-01-12
> **Thelasko said:**
> It appears this piece of software is written specifically for i386 architecture.  It interfaces with the kernel so it isn't portable to other architectures without a rewrite.

I was about to recommend that you file a bug report (and still do), when I discovered [this bug]("https://bugs.launchpad.net/ubuntu/+source/sl-modem/+bug/151562").  A hack is posted that tells you how to install a version from Debian that supports amd64.  Debian is very similar to Ubuntu, so it should work fine.  I recommend you comment on this bug and click the "this affects me" button to let the developers know they need to step up support on this.

Thanks a lot: it installed smoothly. Now I must discover why the slarm module doesn't load...:(
One step by time...

Fabio

---

