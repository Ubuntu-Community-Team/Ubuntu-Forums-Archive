---
title: "I think I have installed 32bit Ubuntu on a 64bit machine how can I tell?"
date: 2009-05-09
forum: x86 64-bit Users
---

### Post by Robster2 on 2009-05-09
I have a Toshiba Satellite AMD 64 x 2 


How can I tell if I have installed the 32bit version or 64bit version?

---

### Post by Wiebelhaus on 2009-05-09
```
sudo aptitude install sysinfo
```

For GUI. then check system tools

Cheers

---

### Post by Robster2 on 2009-05-09
Thanks

Installed Sysinfo

Under System

GNOMEE 2.26.1 (Ubuntu 2009-04-14)
Kernel 2.6.28-11-generic (#42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009)
CGG 4.3.3 (x86_64-linux-gnu)

So does the last line mean that this is 64bit ?

---

### Post by Robster2 on 2009-05-09
Thanks

Installed Sysinfo

Under System

GNOMEE 2.26.1 (Ubuntu 2009-04-14)
Kernel 2.6.28-11-generic (#42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009)
CGG 4.3.3 (x86_64-linux-gnu)

So does the last line mean that this is 64bit ?

---

### Post by jespdj on 2009-05-09
Yes. You can also type:
```
uname -m
```
in a terminal. If it says "x86_64", then you're using 64-bit Ubuntu.

---

### Post by Robster2 on 2009-05-09
> **jespdj said:**
> Yes. You can also type:
```
uname -m
```
in a terminal. If it says "x86_64", then you're using 64-bit Ubuntu.

Doesn't that just tell you what hardware you are running?

man uname

 -m, --machine
  print the machine hardware name

---

### Post by jespdj on 2009-05-09
No, it tells you what version of Ubuntu you are running. It does not tell you if your processor is 32-bit or 64-bit, despite what the man page for uname says.

---

### Post by John.Michael.Kane on 2009-05-09
> **Robster2 said:**
> Doesn't that just tell you what hardware you are running?

man uname

 -m, --machine
  print the machine hardware name

To see a list of your hardware use the below command, This will also show you hardware as 64, or 32-bit look at the width number listed.
```
sudo lshw
```

To list usb hardware use the below command.
```
lsusb
```

For pci devices.
```
lspci
```

For CPU info only use the below command.
```
cat /proc/cpuinfo
```

Hope that helps.

---

### Post by Dark Aspect on 2009-05-09
> **Robster2 said:**
> CGG 4.3.3 (x86_64-linux-gnu)

You are using 64-bit Ubuntu.

---

