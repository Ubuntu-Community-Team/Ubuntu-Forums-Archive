---
title: "firefox 1.0.7 ubstable"
date: 2005-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by tomislavmedak on 2005-10-19
firefox on my ibook g4 800Mhz is very unstable. it crashes too often on me and this is annoying. i'd like to replace it with 1.5 rc2. did anyone try to build it from source and did it work? are there packages available to install it from?

---

### Post by chanders on 2005-10-20
I would try to find the deb for 1.05 as compiling from source can be very tedious.....

---

### Post by aysiu on 2005-10-20
You don't need to build it from source. Just follow the instructions here:

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by tomislavmedak on 2005-10-21
i've upgraded to 1.5 rc 2, but my firefox kept crashing. when i ran the firefox from the terminal, the crash produced the following error message:

```
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadShmSeg (invalid shared segment parameter)'.
  (Details: serial 31 error_code 172 request_code 149 minor_code 2)
```

googling for the error message, i found a debian thread explaining that this was a known issue with the GNUflash killing firefox and bunch of other browsers.

[http://lists.debian.org/debian-amd64/2005/07/msg00428.html](http://lists.debian.org/debian-amd64/2005/07/msg00428.html)

after unistalling the GNUflash firefox worked again fine.

did anyone manage to get the GNUflash or swf-player to work decently on a PPC?

---

