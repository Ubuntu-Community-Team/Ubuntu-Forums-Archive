---
title: "How does one check AMD64"
date: 2006-06-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Giorgis on 2006-06-03
How does one check if an executable is compiled to run for amd64 or plane 32bit x86 ?

And for any other platform for that matter ?

tanx guys

Giorgis

---

### Post by joe_bruin on 2006-06-03
The commandline program 'file' is an easy way to do it.

example:
```
$ file /bin/ls
/bin/ls: ELF 64-bit LSB executable, AMD x86-64, version 1 (SYSV), for GNU/Linux
2.6.0, dynamically linked (uses shared libs), stripped
```

---

### Post by henriquemaia on 2006-06-03
[quote=joe_bruin]The commandline program 'file' is an easy way to do it.

example:
```
$ file /bin/ls
/bin/ls: ELF 64-bit LSB executable, AMD x86-64, version 1 (SYSV), for GNU/Linux
2.6.0, dynamically linked (uses shared libs), stripped
```[/quote]

Nice tip, thanks.

---

