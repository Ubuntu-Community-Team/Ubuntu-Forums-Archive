---
title: "AMD64 + nVidia twin-view = broken gnome-terminal"
date: 2007-04-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by rotten777 on 2007-04-28
Fresh install, enabled the proprietary drivers, then tried to launch gnome-terminal. No modifications to Ubuntu whatsoever.

from ~/.xsession-errors:
```
The program 'gnome-terminal' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 100 error_code 2 request_code 78 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

---

### Post by rotten777 on 2007-04-29
I've found a bug listing.

[https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232](https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232)

If you run into this issue, install xterm via synaptic, edit your X configuration and disable composite:

```
Section "Extensions"
Option "Composite" "false"
EndSection
```

Kinda sad that this big has been found and still made its way into a new release. Especially with an easy fix.

:(

---

