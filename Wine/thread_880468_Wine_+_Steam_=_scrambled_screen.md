---
title: "Wine + Steam = scrambled screen"
date: 2008-08-05
forum: Wine
---

### Post by SGoodyer on 2008-08-05
This has been my first attempt Linux and Wine. I have Wine etc installed correctly along with video drivers.

When I go to download/install a game my whole screen goes all scrambled like a checkerboard with desktop still visible, but broken into squares and placed diagonally. Everything else in Steam works without causing problems.

Using the latest Wine which I just downloaded today.

E8400
ATI 4870 - Catalyst 8.7 (fully working)

---

### Post by Spydr4590 on 2008-08-05
Nm

---

### Post by SGoodyer on 2008-08-05
> **Spydr4590 said:**
> Nm

...?

---

### Post by JUMBODUMBO on 2008-08-05
You need to use Catalyst 8.5 or earlier. Later versions don't work with Wine.

---

### Post by Puinsai on 2008-08-05
I've had this same problem! Thanks for finding the answer! Since I'm new to Linux I need to figure out how to uninstall the drivers :P

Thanks again!

---

### Post by bg86 on 2008-08-21
I have the same problem and would like to know the method in which you corrected the problem if at all.

8.5 catalyst wasn't working for me

---

### Post by brutos on 2008-08-27
im having the same problem and i dont know how to fix it. tried a lot of things but.... nothing. Everything else works great, compiz, all kind of 3d tests. I have ATI 3850 and 8.5 catalyst driver.

Someone please help, i **need** to play DOD source :D

---

### Post by Melcar on 2008-08-27
8.4-8.5 are the last known drivers to work with Wine.  HD4K users are a bit out of luck since I think 8.6 was the earliest driver to support those cards.

---

### Post by paco_strano on 2008-09-04
> **brutos said:**
> im having the same problem and i dont know how to fix it. tried a lot of things but.... nothing. Everything else works great, compiz, all kind of 3d tests. I have ATI 3850 and 8.5 catalyst driver.

Someone please help, i **need** to play DOD source :D
Got the same problem with my ATI 3850 it's glichy
I wonder if the drivers really support that series of video card

---

### Post by blaise69 on 2008-09-09
Same problem here, would really like a fix for this.

Earlier drivers don't appear to help

---

### Post by ObiWan2001 on 2008-09-13
The solution is to change the libGL.so with the one from mesa or the one from 8.5 (DRI and Hardware accerlation works with both)

If you used the ATI-binary installer:
```

sudo mv /usr/lib/xorg/libGL.so.1.2 /usr/lib/xorg/fglrx_org_libGL.so.1.2
sudo cp /usr/lib/FGL.renamed.libGL.so.1.2 /usr/lib/xorg/libGL.so.1.2

```

with 64bit:
```

sudo mv /usr/lib64/xorg/libGL.so.1.2 /usr/lib64/xorg/fglrx_org_libGL.so.1.2
sudo cp /usr/lib64/FGL.renamed.libGL.so.1.2 /usr/lib64/xorg/libGL.so.1.2
sudo mv /usr/lib32/xorg/libGL.so.1.2 /usr/lib32/xorg/fglrx_org_libGL.so.1.2
sudo cp /usr/lib32/FGL.renamed.libGL.so.1.2 /usr/lib32/xorg/libGL.so.1.2

```

As alternative you can use the libGL.so from the 8.5 driver:
Download the 8.5 driver from AMD
```

sh ati-driver-installer-8-5-x86.x86_64.run --extract tmp
```
32bit:
```

sudo cp tmp/arch/x86/usr/X11R6/lib/libGL.so.1.2 /usr/lib/xorg/libGL.so.1.2

```
64bit:
```

sudo cp tmp/arch/x86_64/usr/X11R6/lib64/libGL.so.1.2 /usr/lib64/xorg/libGL.so.1.2
sudo cp tmp/arch/x86/usr/X11R6/lib/libGL.so.1.2 /usr/lib32/xorg/libGL.so.1.2

```

---

