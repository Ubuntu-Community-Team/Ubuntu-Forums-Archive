---
title: "Broadcom wireless problems"
date: 2008-09-25
forum: x86 64-bit Users
---

### Post by ludu900 on 2008-09-25
I have a 64 bit amd and a bcm4328 network card.  The ndiswrapper driver that i could use to fix the problem doesnt work with 64 bit amd. Any advice??

---

### Post by pytheas22 on 2008-09-25
Did you look for a 64-bit Windows driver?  As long as you can find one, you should be able to use it with ndiswrapper.

There are also native drivers that you might be able to use, depending on the exact chipset.  Please post the output of this command so that we can figure out exactly which chip you have:

```
lspci -nn
```

---

### Post by opr8ive on 2008-09-26
> **ludu900 said:**
> I have a 64 bit amd and a bcm4328 network card.  The ndiswrapper driver that i could use to fix the problem doesnt work with 64 bit amd. Any advice??

```
jason@sisyphus:~$ ndiswrapper -l
bcmwl5 : driver installed
    device (14E4:4328) present
jason@sisyphus:~$ 
```


64 bit Ubuntu 8.04

For this, I just followed the tutorial [here...]("https://help.ubuntu.com/community/WifiDocs/NdiswrapperOnAMD64")

-Jason

---

