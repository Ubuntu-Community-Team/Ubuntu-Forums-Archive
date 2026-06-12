---
title: "Driver instalation"
date: 2009-02-01
forum: x86 64-bit Users
---

### Post by skin480 on 2009-02-01
Hello

I just instal ubuntu 8.04 and I need to know how to instal the driver for a Gigabyte Ati HD 2600 Pro video card.
Another driver problem is for a Tv tuner Leadtek WinFast 2000 XP, I haven't find it anywhere.

Plz help a beginner :-k

Tnx

---

### Post by cariboo on 2009-02-01
Go to System-->Administration-->Hardware Drivers and enable the recommended non-free driver. 

For you TV tuner card  could you open a Applications-->Accessories-->Terminal and type:

```
sudo lshw -C multimedia
```

This will list the details of you TV tuner card and what driver it is using. Please enclose the output in [noparse]```

```[/noparse] tags to make it easier to read.

Jim

---

### Post by shadowhacker on 2009-02-02
> I just instal ubuntu 8.04 and I need to know how to instal the driver for a Gigabyte Ati HD 2600 Pro video card.

Is that an AGP or PCIe card? If it's AGP and works on Ubuntu with no crashes, please let me know. I have had nothing but problems with the PCIe-to-AGP crossover cards on windoze. I just ordered 2 ATI Radeon 9800XT 256 cards because I saw them on eBay, and figured it would be my last chance ever to get the last good true AGP card.

Sorry to bring another topic into the mix, just curious.

---

