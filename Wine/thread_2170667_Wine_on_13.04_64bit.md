---
title: "Wine on 13.04 64bit"
date: 2013-08-27
forum: Wine
---

### Post by echo6-uk on 2013-08-27
Wine refuses to work, and I believe the issue is related to 64bit.  When executing wine I get ```
$ wine --help
bash: /usr/bin/wine: cannot execute binary file
```

I have ia32-libs and ia32-libs-multiarch installed.

```
$ wine64 --version
wine-1.6
```

---

### Post by sanderj on 2013-08-27
Hi,

13.04 64-bit here too, but different results:

```

sander@R540:~$ uname -a
Linux R540 3.8.0-29-generic #42-Ubuntu SMP Tue Aug 13 19:40:39 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
sander@R540:~$ 

sander@R540:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring
sander@R540:~$ 

sander@R540:~$ wine --help
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
sander@R540:~$ wine --version
wine-1.4.1
sander@R540:~$ 
sander@R540:~$ wine64 --version
wine-1.4.1
sander@R540:~$ 

```

How did wine-1.6 get on your 13.04?

---

### Post by echo6-uk on 2013-09-01
I've resolved my issue, I had forgotten to include CONFIG_IA32_EMULATION in my kernel config.

To get wine-1.6 you need to add the repository and update, then specify the version you want to install.  [[URL]http://www.winehq.org/download/ubuntu]([URL]http://www.winehq.org/download/ubuntu)[/url]

---

