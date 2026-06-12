---
title: "totem kills X (Signal 11)"
date: 2005-12-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by HankB on 2005-12-20
Starting Totem or gxine or apparently other video display programs causes X to exit with a signal 11. From the log:

```

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Fatal server error:
Caught signal 11.  Server aborting


Please consult the The X.Org Foundation support
         at http://wiki.X.Org
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional informati on.



```This is on a laptop with an ATI  Radeon Xpress 200M. I'm using the ATI driver that comes with Breezy which identifies itself:
```
root@baobab:/etc/X11# xdpyinfo
name of display:    :0.0
version number:    11.0
vendor string:    The X.Org Foundation
vendor release number:    60802000
X.Org version: 6.8.2

``` 

At  the beginning of the X log I find:
```
X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174819 root@crested.warthogs.hbd.com)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.8.1 x86_64 [ELF]
Current Operating System: Linux baobab 2.6.12-10-amd64-generic #1 Fri Nov 18 11:51:07 UTC 2005 x86_64
Build Date: 10 October 2005
        Before reporting problems, check http://wiki.X.Org
        to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-amd64-generic (buildd@king) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Fri Nov 18 11:51:07 UTC 2005 T
```

and further on

```
(II) LoadModule: "ati"
(II) Loading /usr/X11R6/lib/modules/drivers/ati_drv.o
(II) Module ati: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 6.5.6
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 0.7
```

There's more, but it is rather voluminous. I can provide it if useful.

Signal 11 used to indicate bad RAM. I would hope not. I have 2 GB Crucial ram which is underclocked in this application. Other than this, the machine is rock solid.
 
I understand that I can download a driver from ATI, but it is not clear that it supports suspend. I really need suspend on this machine.

Any suggestions are most appreciated.

thanks,
hank

---

