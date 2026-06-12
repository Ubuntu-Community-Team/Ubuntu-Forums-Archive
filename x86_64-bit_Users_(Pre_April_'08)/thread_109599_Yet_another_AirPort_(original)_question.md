---
title: "Yet another AirPort (original) question"
date: 2005-12-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by lincoln-white on 2005-12-28
Hello all,

I have an original Blueberry iBook with an original AirPort card, which was working under MacOS 9.x. I installed Ubuntu, but it apparently hasn't recognized my AirPort card. Another random fact, in case this helps/is useful: lsmod reveals that the airport modules aren't being loaded. Further, I don't see the "Add" button in the network app to add another network device. Any expert advice? I sure could use it.

Thanks,

jlw

---

### Post by narcolept on 2005-12-28
I believe Airport uses Broadcom chipsets, in which case the drivers would have to be loaded through ndiswrapper.  You can probably find out the exact chipset by googling for your model and airport chipset. After that, there's several threads on this forum about ndiswrapper for wireless drivers.

---

### Post by khc on 2005-12-29
What happens if you try to load the airport module manually?

---

### Post by lincoln-white on 2005-12-29
No changes if I load the airport modules directly (eg running modprobe airport). It doesn't seem that the system is even aware of the card, though. lspci and lshw show nary a mention of the airport card. Shouldn't it show up somewhere?

Thanks,
jlw

---

### Post by chascon on 2006-01-12
> I believe Airport uses Broadcom chipsets, in which case the drivers would have to be loaded through ndiswrapper. You can probably find out the exact chipset by googling for your model and airport chipset. After that, there's several threads on this forum about ndiswrapper for wireless drivers.

You're thinking of "Airport Extreme", not the original.  And there is no ndiswrapper for ppc.  There are however native linux drivers for AE now, as there should be for the original Airport.

---

### Post by ssam on 2006-01-13
hmmm. it should work fine.

i just had a look at lspci and lshw. i can't see my airport card in either (i have a titanium powerbook).

does it show up in
```
iwconfig
```
or
```
ifconfig -a
```

---

### Post by lincoln-white on 2006-01-13
I have gotten this card to work without fuss simply by resetting the pram.

jlw

---

