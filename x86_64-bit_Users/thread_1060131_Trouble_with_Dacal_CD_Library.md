---
title: "Trouble with Dacal CD Library"
date: 2009-02-04
forum: x86 64-bit Users
---

### Post by scotland0208 on 2009-02-04
Hello, I just installed Ubuntu 8.10 and I have a Dacal CD Library (it is a USB device that has software that allows me to store and recall CD/DVD's). The problem I'm having is that after I get the software to work, it requires me to have the unit plugged it. This confused me because it is plugged in, it's always plugged in. Anyway, I would like to know how to get my Ubuntu to see it.

---

### Post by cariboo on 2009-02-04
With some Windows programs you have to plug the device in after you have installed the software in order for the software to detect the device. If you get this working and there isn't an entry already, you may want to add an entry  for the software at [WineHQ]("http://appdb.winehq.org/").

Jim

---

### Post by pyalot on 2009-06-11
I've written a device driver/daemon and an iphone/ipod touch webapp to access the CD Library II from Dacal. You can use it to browse/retrieve/store your media, it supports multiple devices and can identify each device uniquely (so no trouble with replugging the devices etc.).

The repository for the software can be found at [http://hg.codeflow.org/mediab](http://hg.codeflow.org/mediab)

The complete stuff is written in python, but since it's 3 days old and I'm the only user there's no website or instructions, but if you need help in setting it up, don't be afraid to tell me what you need at [EMAIL="pyalot@gmail.com"]pyalot@gmail.com[/EMAIL]

Cheers

---

