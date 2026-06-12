---
title: "[SOLVED] No boot menu"
date: 2008-06-01
forum: x86 64-bit Users
---

### Post by geum on 2008-06-01
Ubuntu 8.04(hardy)

I have two hdds, Ubuntu(hardy) on sda, and pcBSD on sdb.
But I dont have a boot menu it boots straight into Ubuntu,when I change the boot order in bios it then boots straight into pcBSD, again without a menu.
I am not sure if pcBSD uses grub as its loader.
I installed pcBSD first and Ubuntu last,so I am surprised that Ubuntu failed to recognise the other o/s.

---

### Post by logos34 on 2008-06-01
You might need to change the 'timeout' and/or comment out 'hiddenmenu' option:
[http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst](http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst)

PC-BSD uses it's own bootloader.  (although I think Free-BSD switched to grub a while back, unless I'm confusing it with another distro)

If BSD isn't listed at the bottom of menu.lst, you should be able to simply add an entry to [chainload]("http://users.bigpond.net.au/hermanzone/p15.htm#2._Chainloader") it, so you don;t have to toggle the Bios boot disk every time

---

### Post by geum on 2008-06-01
logus34

Working fine now,commented out "hiddenmenu"and changed "timeout".
Thank you for your help and for that grub link,very interesting.

---

