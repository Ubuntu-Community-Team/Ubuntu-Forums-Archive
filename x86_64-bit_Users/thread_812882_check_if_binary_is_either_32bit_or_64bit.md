---
title: "check if binary is either 32bit or 64bit"
date: 2008-05-30
forum: x86 64-bit Users
---

### Post by monkeyking on 2008-05-30
How do I check how if a binary executable is compiled for 64 bit,


thanks.

---

### Post by Rinzwind on 2008-05-30
From commandline:
file {filename}
It'll show 

ELF 32-bit LSB executable

for a 32 bit and mostlikely 64 bit for a 64 bit?

If not please correct me someone :)

---

### Post by felker2 on 2008-05-30
You can use

```

file `which perl`

```

to get info about the executable perl. The 'which'-command will find the correct path to that executable. BTW Please note the back-ticks in the command.

Result:

```

sander@ubuntu804:~$ file `which perl`
/usr/bin/perl: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped
sander@ubuntu804:~$

```

---

