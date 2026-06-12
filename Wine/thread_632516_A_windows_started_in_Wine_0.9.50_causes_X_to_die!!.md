---
title: "A windows started in Wine 0.9.50 causes X to die!!!"
date: 2007-12-05
forum: Wine
---

### Post by nick2000 on 2007-12-05
I was using a Windows application that I wrote with JBuilder under Wine 0.9.46 in Ubuntu 7.10 64. While the display was weird in seamless mode, it was running OK.
I upgraded to 0.9.50 and when I start the application, the screen goes black and I get thrown to the prompt.
So, basically X dies.

Wine people told me it was not their problem but the distribution's problem since they "cannot kill X". I understand that if they pass bad parameters, X is supposed to survive.

I am using Wine with the default settings and ran wineprefixcreate.

Here are my logs:

Dmesg | tail shows:
[15536.637180] mtrr: no more MTRRs available

Wine application.exe's stderr is:
fixme:win:EnumDisplayDevicesW ((null),0,0x33b14c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x33b14c,0x00000000), stub!
X connection to :0.0 broken (explicit kill or server shutdown).
X connection to :0.0 broken (explicit kill or server shutdown).


Note that no crash file is created.


Xorg.0.log has these lines at the end:
Backtrace:
0: /usr/bin/X(xf86SigHandler+0x6d) [0x48670d]
1: /lib/libc.so.6 [0x2abee09967d0]
2: /usr/lib/dri/i965_dri.so [0x2abef35f15cb]
3: /usr/lib/xorg/modules/extensions//libglx.so(DoRender+0x13b) [0x2abee1c6845b]
4: /usr/lib/xorg/modules/extensions//libglx.so [0x2abee1c6c00d]
5: /usr/bin/X(Dispatch+0x1db) [0x4514eb]
6: /usr/bin/X(main+0x45d) [0x439f4d]
7: /lib/libc.so.6(__libc_start_main+0xf4) [0x2abee0982b44]
8: /usr/bin/X(FontFileCompleteXLFD+0x231) [0x439249]

Fatal server error:
Caught signal 11.  Server aborting

(II) AIGLX: Suspending AIGLX clients for VT switch
(II) intel(0): xf86UnbindGARTMemory: unbind key 0
(II) intel(0): xf86UnbindGARTMemory: unbind key 1
(II) intel(0): xf86UnbindGARTMemory: unbind key 2
(II) intel(0): xf86UnbindGARTMemory: unbind key 3
(II) intel(0): xf86UnbindGARTMemory: unbind key 4

Maybe there is a better place to post this?

---

