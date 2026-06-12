---
title: "beryl wont work"
date: 2007-08-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by sniffysniper on 2007-08-28
well i installed it but nothing is happening not after installing... i want it like they have it on youtube or sort of that

---

### Post by John.Michael.Kane on 2007-08-28
> **sniffysniper said:**
> well i installed it but nothing is happening not after installing... i want it like they have it on youtube or sort of that

You can try this.

Step 1
Make sure your gpu drivers are properly installed.

Step 2
```
sudo nvidia-xconfig --add-argb-glx-visuals --composite
```

Step 3
```
sudo aptitude install beryl emerald-themes beryl-manager
```

Step 4
reboot the machine, and log back in.

Step 5
Press alt+f2, and type beryl-manager into the box that shows up.

Step 6 Work around should the title bars be missing
Right click on Beryl Manager>Advanced Beryl Options>Rendering Path>Copy.

---

### Post by sniffysniper on 2007-08-28
i tired somethings and played around with it and now it works still cant get a cool theme to work rest is working i dont know how to set a theme can you please tell me that=

---

### Post by maxamillion on 2007-08-28
Beryl is dead, you might want to look into using Compiz Fusion.

[http://www.opencompositing.org/](http://www.opencompositing.org/)

Enjoy.

---

### Post by John.Michael.Kane on 2007-08-28
> **maxamillion said:**
> Beryl is dead, you might want to look into using Compiz Fusion.

[http://www.opencompositing.org/](http://www.opencompositing.org/)

Enjoy.

beryl is not dead. in fact right on the very site you link to it states the following.

Beryl is a Compiz fork, now discontinued, **but still supported.**

---

### Post by John.Michael.Kane on 2007-08-28
> **sniffysniper said:**
> i tired somethings and played around with it and now it works still cant get a cool theme to work rest is working i dont know how to set a theme can you please tell me that=

Right click on beryl manager. Then click on emerald theme manager, and select the theme you want.

To adjust other settings click on beryl settings manager.

---

### Post by sniffysniper on 2007-08-28
although still dont get how to get it to work+ to have the good options isntalled

---

### Post by John.Michael.Kane on 2007-08-28
> **sniffysniper said:**
> although still dont get how to get it to work+ to have the good options isntalled

You will have play with the settings, As everyone settings is different, and not universal.

---

