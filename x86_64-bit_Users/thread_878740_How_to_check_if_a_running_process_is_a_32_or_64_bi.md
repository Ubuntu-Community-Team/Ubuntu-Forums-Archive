---
title: "How to check if a running process is a 32 or 64 bit image?"
date: 2008-08-03
forum: x86 64-bit Users
---

### Post by vishalrao on 2008-08-03
Hello,

How do I check if a running process is a 32 bit or 64 bit image/program? I'm running Hardy amd64.

For example, if I compile a small executable with "gcc -m32" or something like that?

I would like to check some running processes like Firefox and OpenOffice.org...

Thanks,
Vishal

---

### Post by felker2 on 2008-08-03
Let's first check the bit-ness of perl:

```

sander@ubuntu804:~$ which perl
/usr/bin/perl

sander@ubuntu804:~$ file /usr/bin/perl
/usr/bin/perl: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped
sander@ubuntu804:~$

```

To check the bit-ness of running processes: take the output from "ps -ef" and then use the "file ..." method. For example:


```

sander@ubuntu804:~$ ps -ef  | tail
root     17232  5272  0 21:08 ?        00:00:00 sshd: sander [priv]
sander   17235 17232  0 21:08 ?        00:00:00 sshd: sander@pts/2
sander   17237 17235  0 21:08 pts/2    00:00:00 -bash
www-data 17960  6123  0 21:13 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 18090  6123  0 21:18 ?        00:00:00 /usr/sbin/apache2 -k start
sander   18204 17237  0 21:22 pts/2    00:00:00 ps -ef
sander   18205 17237  0 21:22 pts/2    00:00:00 -bash
sander   18464  6650  0 Aug02 pts/4    00:00:00 /bin/bash
sander   18715  6650  0 Aug02 pts/6    00:00:00 /bin/bash
sander   18975  6650  0 Aug02 pts/0    00:00:00 /bin/bash
sander@ubuntu804:~$ file /usr/sbin/apache2
/usr/sbin/apache2: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped
sander@ubuntu804:~$

```

---

### Post by Kilz on 2008-08-03
> **vishalrao said:**
> Hello,

How do I check if a running process is a 32 bit or 64 bit image/program? I'm running Hardy amd64.

For example, if I compile a small executable with "gcc -m32" or something like that?

I would like to check some running processes like Firefox and OpenOffice.org...

Thanks,
Vishal

Check if you wish, but the Ubuntu packages for Firefox and Open Office are 64bit since Feisty. Firefox has been 64bit all along, Open office got a 64bit version in Feisty.

---

### Post by nanonils on 2008-10-19
> **Kilz said:**
> Check if you wish, but the Ubuntu packages for Firefox and Open Office are 64bit since Feisty. Firefox has been 64bit all along, Open office got a 64bit version in Feisty.

I can confirm this. I've been going through beta install frenzies of all sorts of applications, including openoffice3 only realize that after the most recent Intrepid 64 bit update today my that office has vanished form my HD (it is literally nowhere to be found - I'm mystified). So I went ahead and picked the official 2.4.1. version from the repositories which has the [http://go-oo.org/](http://go-oo.org/) ODF and MS optimized interface ([http://en.wikipedia.org/wiki/Go-oo](http://en.wikipedia.org/wiki/Go-oo)). Because it was such a hassle to find the correct beta-version before its official release I wanted to double check whether I now have a 64 bit or not and I get: 

I@my-laptop:~$ file /usr/lib/openoffice/program/soffice.bin
/usr/lib/openoffice/program/soffice.bin: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped

I'll stick with the official repositories form now on: office runs more stable and is better integrated. I'll sit and wait till oo3 shows up in there. There were a lot of dependency issues when I installed on my own and as of today my T61 trackpoint, trackpoint scroll and Skype are suddenly working again!

---

