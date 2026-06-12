---
title: "gnome-terminal crashes :-(  error inside:"
date: 2007-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by AntiRush on 2007-10-26
gnome-terminal recently stopped working.  From a shortcut it just silently fails.  When I try to start it from aterm I get this error:

```

The program 'gnome-terminal' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 111 error_code 2 request_code 78 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

Any ideas?  Google turned up this: [https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/138605](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/138605) but there doesn't seem to be a resolution.

---

### Post by Superkuh on 2007-10-26
Checking here *might* help:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232)

I had similar issues in an old install and just gave up and compiled rxvt-unicode. ([https://answers.launchpad.net/ubuntu/+source/gnome-terminal/+question/9430](https://answers.launchpad.net/ubuntu/+source/gnome-terminal/+question/9430))

---

