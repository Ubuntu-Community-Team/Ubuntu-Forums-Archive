---
title: "Ubuntu 8.04, Wine and Segmentation fault"
date: 2008-05-06
forum: Wine
---

### Post by muchacho1 on 2008-05-06
Hi!
After update to 8.04 Wine does not work. I tried to purge it, but it does not help.

```
muchacho@ubuntu:~$ winecfg
wine: creating configuration directory '/home/muchacho/.wine'...
err:seh:setup_exception_record stack overflow 908 bytes in thread 0012 eip b7cad246 esp 00240fa4 stack 0x240000-0x241000-0x340000
Segmentation fault
```

Thanks for help.

---

### Post by carusoswi on 2008-06-15
> **muchacho1 said:**
> Hi!
After update to 8.04 Wine does not work. I tried to purge it, but it does not help.

```
muchacho@ubuntu:~$ winecfg
wine: creating configuration directory '/home/muchacho/.wine'...
err:seh:setup_exception_record stack overflow 908 bytes in thread 0012 eip b7cad246 esp 00240fa4 stack 0x240000-0x241000-0x340000
Segmentation fault
```

Thanks for help.

Will ever there be any help for us wine users in 8.04, or am I destined to relying soley on XP to run those few MS aps that I must use?

Caruso

---

### Post by pjimenez on 2008-08-20
You should use the winehq .deb's from [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

They work quite well!

---

