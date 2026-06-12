---
title: "PCTel/Linmodem Support?"
date: 2006-08-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by schnarff on 2006-08-15
I've been trying for the better part of the day to get a fax modem installed, with a pair of Linmodems (output from scanModem):
```

Class 0703: 134d:7897   Modem: PCTel Inc HSP MicroModem 56 (rev 02) (prog-if 01 [Hayes/16450])
  SubSystem 134d:0001  PCTel Inc: Unknown device 0001


Class 0780: 14f1:1033   Communication controller: Conexant HCF 56k Data/Fax Modem (rev 08)
  SubSystem 1092:0abe  Diamond Multimedia Systems: Unknown device 0abe
```

It looks like both of these are supported under Linux, via PCTel and Linuxant, respectively...IF I was on a regular old x86 system, instead of x86_64. The Linuxant people have explicitly told me that their software won't work on AMD64...but the PCTel part is a bit more interesting. Specifically, configure fails due to this issue, documented in their FAQ:

```
16. Message "include/asm/mach-default directory could not be found" (2.6)
-------------------------------------------------------------------------
The link include/asm must have been setup to link to your specific machine architecture.  This module is designed to use include/asm-i386 and in particular it is dependant upon irq_vectors.h in include/asm/mach-default.

The link include/asm is also created by the kernel Makefile, often when "make [ANY]config" is used.  You probably need to configure you kernel first and maybe compile it too.
```

I see that include/asm points to asm-x86_64. Unfortunately, there is no mach-default directory in there, nor even an irq_vectors.h.  Thus, my questions are:

* Does this file exist for AMD64, and if so, how do I acquire it? Am I stuck reconfiguring/recompiling my kernel, or is there a simpler way to do it?

* If I can't get my hands on this file, and am thus unable to compile the PCTel driver, is there any other way to get support for that modem?

* Assuming that I can't get Linmodem support, is there a list of supported hardware modems for Ubuntu AMD64?

Thanks,
Alex Kirk

---

### Post by helmut_hed on 2006-08-24
Hi!

You have an interesting problem...  PCTel modem drivers contain a binary "blob" of regular x86 code that the maintainers don't have source for.  All the same, AMD64 is a superset of regular x86, so it *might* work...  depends on how the kernel handles this stuff.

If you want to give it a try, I think you need some additional kernel header packages - perhaps this one?

[http://packages.ubuntu.com/dapper/devel/linux-headers-2.6.15-23-amd64-k8](http://packages.ubuntu.com/dapper/devel/linux-headers-2.6.15-23-amd64-k8)

(assuming you're using Dapper).  There's also an amd64-generic, I guess if you are using compatible Intel chips you could go with that.

Good luck!
Jeff

---

