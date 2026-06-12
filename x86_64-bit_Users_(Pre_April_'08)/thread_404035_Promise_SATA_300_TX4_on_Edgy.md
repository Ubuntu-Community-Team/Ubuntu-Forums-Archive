---
title: "Promise SATA 300 TX4 on Edgy?"
date: 2007-04-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by fiztlen on 2007-04-07
I've picked up a SATA 300 TX4 from Promise that I'm trying to get working with Edgy Eft x64.  I've found a number of sets of instructions, and managed to mess things up trying to follow them.  They also seem aimed towards earlier releases, with notes that by now the card should "just work".

My latest attempt is with the [promise x64 source driver]("http://www.promise.com/support/download/download2_eng.asp?productID=139&category=all&os=100"), which terminates with this message:
```
make[2]: *** [/usr/local/src/ut_mod/pdc-ulsata2.o] Error 1
make[1]: *** [_module_/usr/local/src/ut_mod] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make: *** [default] Error 2
```

The [wiki page that seems relevant]("https://wiki.ubuntu.com/HardwareSupportComponentsSerialATAControllers") only has one entry, for a 3ware card.

Can someone please point me towards a current guide?

Thanks much,
Len

---

