---
title: "No such file or directory"
date: 2007-05-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by tim042849 on 2007-05-24
Using kubuntu 7.04 amd 64
I've downloaded a 32-bit binary - it is called
rebol
and is an interpreter for the rebol programming language
It is not available from the repositories.
when I attempt to execute it I get
"""
No such file or directory
"""
it runs on slackware 10.0 just fine
  on slackware ldd rebol says that it needs
      libm.so.6 and libc.so.6, which are available on
      the ubuntu machine

ldd rebol on ubuntu gives me
"Not a dynamic executable"
linux32 rebol gives me
"Can not execute rebol: No such file or directory"
permissions are 775, it *is* on path, `which rebol' verifies the path and
I've tried both /usr/bin and /usr/local/bin as well as running from 
arbitrary directories as ./rebol
Question:
Is this a 64-bit compatiblity problem?
Thanks
Tim

---

### Post by kuja on 2007-05-24
I'm not sure, but I *have* seen this before once, I think it was with the RealPlayer installer. Can't recall if anyone found a solution or not though.

---

