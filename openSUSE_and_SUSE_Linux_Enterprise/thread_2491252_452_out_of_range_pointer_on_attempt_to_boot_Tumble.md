---
title: "452: out of range pointer on attempt to boot Tumbleweed 64 bit"
date: 2023-10-02
forum: openSUSE and SUSE Linux Enterprise
---

### Post by maketopsite on 2023-10-02
Leap 15.5 grub, command line (reached by pressing C in grub):

```
insmod luks
cryptomount hd0,4
set root=(crypto0)
...
set prefix=(crypto0)/boot/grub2
insmod normal
normal

....
Loading Linux 6.5.4-1-default
452: out of range pointer 0xcabb8010
Aborted: Press any key to exit.
```
(simplified output)

Is it please possible to run TW from Leap's grub ?

---

### Post by Rubi1200 on 2023-10-02
I'm confused. Do you have it installed or you want to install it?

> 452: out of range pointer 0xcabb8010
Aborted: Press any key to exit.


I've seen this error recently but that was when booting a liveUSB to install a distro. Usually was able to resolve by writing the image in dd mode.

Sorry if that doesn't help just wanted to mention how I resolved the error.

---

### Post by maketopsite on 2023-10-02
> **Rubi1200 said:**
> I'm confused. Do you have it installed or you want to install it?



I've seen this error recently but that was when booting a liveUSB to install a distro. Usually was able to resolve by writing the image in dd mode.

Sorry if that doesn't help just wanted to mention how I resolved the error.

installed 

No problem, thank you for reply.

---

