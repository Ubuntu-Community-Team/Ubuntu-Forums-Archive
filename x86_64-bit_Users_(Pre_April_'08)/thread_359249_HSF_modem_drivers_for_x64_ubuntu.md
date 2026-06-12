---
title: "HSF modem drivers for x64 ubuntu"
date: 2007-02-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by m25 on 2007-02-11
Hello, I am new here and new to linux too, so you'll have to forgive me for anything stupid I say.
I have inheriten an old conexant modem on my new PC and now just can't get it to work on the 64 bit ubuntu.  downloaded some drivers from linuxant.com but all of them didn't install and prompted something like 'wrong kernel i386'.
What can I do to get this modem working?!

---

### Post by amaurynieto on 2007-08-12
Presently, only 32 bit drivers are available free of charge, with full 56k voice data support through DELL. Search my other posts on this, or simply google: "Conexant Deb Dell", and it'll take you there.

It is very sad that 64 bit doesn't get the serious attention it should, and while Linuxant DOES have the capability to set it up on 64 bit (just look around on their webpage), if you don't PAY for the driver, you'll be stuck at 14.4 k, data only.

Fortunately for all, since Dell got on the Ubuntu wagon, they have the HSFmodem DEB drivers on their webpage, which I'm pleased to say work on MOST conexant modems. The only issue is, they haven't compiled
a 64 bit driver. It presently only works on 32 bit.

Is this a bummer? Very much so. I've asked through ideastorm.com to have them open up a 64 bit edition. It's only a matter of time, but for the time being, I had to downgrade from FF 64 to FF 32 to get it working. 

(mind you, I have Cable High Speed, so I've no use for the modem other than faxing through hylafax or efax, however I'd rather ALL the hardware is working on my Inspiron 1501. One never knows if they'll end up in a hotel in the boonies somewhere trying to ooze out a connection through dial-up!)

Lest you're as bummed as I was, I hope this helped you.

---

### Post by amaurynieto on 2007-12-21
Update! - 64 bit drivers are now available in Tarball from linux.dell.com / you need to compile the deb yourself, which can be laborious, however, it's better than nothing... Update as well that 7.10 drivers for the conexant chipset are available, these ARE compiled into a deb for i386 only. 

A great howto about this at [www.ubuntu1501.com](www.ubuntu1501.com)

Cheers, A.

---

### Post by s3a on 2008-03-17
> **amaurynieto said:**
> Update! - 64 bit drivers are now available in Tarball from linux.dell.com / you need to compile the deb yourself, which can be laborious, however, it's better than nothing... Update as well that 7.10 drivers for the conexant chipset are available, these ARE compiled into a deb for i386 only. 

A great howto about this at [www.ubuntu1501.com](www.ubuntu1501.com)

Cheers, A.

Could you please make a .deb of the 64-bit HSF modem driver for Ubuntu 7.10 and send it to me via email or torrent or whatever please?

---

