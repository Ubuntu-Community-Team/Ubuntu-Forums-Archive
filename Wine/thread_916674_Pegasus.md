---
title: "Pegasus"
date: 2008-09-11
forum: Wine
---

### Post by oygle on 2008-09-11
Wine 1.0 and Ubuntu 8.04

Pegasus keeps exiting when I try to send an email (locally). Everything else works okay as it did under XP, although for some reason TLS/STLS won't work for some connections under WINE, yet it will work for other connections under WINE/Pegasus.

All other functions appear to work okay, it is only this problem with WINE exiting when I try to send an email. It's almost as if WINE is sending the following to Pegasus ..

Alt-F4   which closes all windows except the main window
Alt-F4   which exits the program

you can see it doing one, then the other.  Pegasus is not actually crashing, because if it did, the lock file msg would appear, and it does not when you go back into Pegasus. The 'queued mail' can then be sent.

On some occasions though, Pegasus exits without email being sent (locally), it simply closes as it does when an attempt is made to send email (sends an email to the local queue).

Considering the fact that there does not appear to be an email client under Ubuntu that has all the features of Pegasus, I would ask the WINE developers to please fix this problem.

There isn't much output from WINE, when run from the terminal, just the following

```

$ wine winpm-32.exe
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:storage:StgCreateDocfile Transacted mode not implemented.

```

Can someone help please ?

---

### Post by oygle on 2008-09-12
Does anyone have any answers to this problem please ?

---

### Post by oygle on 2008-10-24
Do any WINE developers ever frequent this forum at all ?

---

