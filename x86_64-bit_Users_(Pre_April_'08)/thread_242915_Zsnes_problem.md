---
title: "Zsnes problem"
date: 2006-08-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Chrono86 on 2006-08-24
Hey guys~
Got the newest version of Zsnes compiled and installed with no problems...but when I go to run it I get this error message:

> adam@adam:~$ zsnes
ZSNES vPre 1.43, (c) 1997-2006, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

This is a work in progress build. It contains code which
May or may not be complete
Starting Mouse detection.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
Segmentation fault
adam@adam:~$

If I run it as root I get this:

> root@adam:~# zsnes
ZSNES vPre 1.43, (c) 1997-2006, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

This is a work in progress build. It contains code which
May or may not be complete
Starting Mouse detection.
ManyMouse: 1 mice detected.
Segmentation fault
root@adam:~#

Any ideas as to what that means?
Thanks
Adam

---

