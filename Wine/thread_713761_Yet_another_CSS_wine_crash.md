---
title: "Yet another CS:S wine crash"
date: 2008-03-03
forum: Wine
---

### Post by nuclearpidgeon on 2008-03-03
Hey everyone,

I have an Acer Travelmate 6292 laptop, running ubuntu linux 7.10+windows dualboot.
I installed wine on linux, and installed Steam through the MSI installer. Once installed, I copied all the CS:S GCF files into the steamapps directory, and re-ran steam. It had to download some stuff (the counterstrike source folder w/binaries etc.), then it said 100%.
I clicked play. there was a brief pause, the for no reason whatsoever, wine crashed. This happened using wine 0.9.54 and now using 0.9.49 (it runs css on my other pc much better than 0.9.54

last 5 lines of wine console info (nothing past this updated after clicking play)
```
fixme:win:SetLayeredWindowAttributes (0x10086,0x00000000,150,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10086,0x00000000,150,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10086,0x00000000,0,2): stub!
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1

```

I think the last 2 are of importance - I had a billion and one fixme errors, which were all very similar.

PS
Acer graphics card specs - Mobile Intel Graphics Media Accelerator X3100
IT WORKS. I am using compiz-fusion fine, no glitches or whatever.
i will post other specs if required

---

### Post by Peetke on 2008-03-03
Did you try 0.9.55? It's the latest and maybe the regression is already fixed?
[http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/)

---

### Post by nuclearpidgeon on 2008-03-06
downloading 0.9.56 now. if that doesnt work i'll try 55
I tried 55 on my other PC, but there was a MASSIVE performance drop, so I ent back to 49 for 120+ fps :D

---

### Post by nuclearpidgeon on 2008-03-06
FAIL.

It once again crashed to the desktop, without even saying Preparing to load CSS...
I'm gonna try 0.9.55

EDIT:
Tried 55, same result

NOTE, for these tests i ran metacity --replace before running steam, to avaoid compiz errors

---

### Post by nuclearpidgeon on 2008-03-12
I just biught a maazine, and it has a wine tutorial, with stuff for compiling wine from source. I'm gonna try this and see if it works any better

---

