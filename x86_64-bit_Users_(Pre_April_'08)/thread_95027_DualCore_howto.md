---
title: "DualCore howto?"
date: 2005-11-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Snipersnest on 2005-11-25
Ok so I have an AMD 4400+ dualcore...but 64bit Ubuntu only sees 1 processor.. how can I get it to use all of my processor?

---

### Post by psusi on 2005-11-25
Install the smp kernel.

---

### Post by Snipersnest on 2005-11-26
ok if I install that kernel will I have any problems?? The system seems ok at the moment but is normally faster.  I'd rather leave the stability than increase the bugs... Anything I should keep in mind?
 
Also anybody have a kernel tutorial?

---

### Post by Kango_V on 2005-11-26
Been running the K8 SMP kernel for quite a while now with no problems.

Go to synaptic and enable the hidden repositories.
Settings->Repositories.  Click settings.  Enable the disabled binary repos.

Click OK.

Search for "linux-amd64-k8-smp".  There should be only one package listed.  Right click and mark for installation.  This should bring in 4 packages.

Now install.

Once installed, reboot.  This also brings in the restricted modules for NVidia drivers.

This is all i have ever done on two machines.  One is a home build, the other is an IBM Intellisation A-Pro.  One is dual core and the other dula CPU. 

Have fun.

daz

---

### Post by AndersAA on 2005-11-26
if you have timing problems (although I doubt you will) you can change /boot/grub/menu.lst

Where it says nonaltoptions, add notsc.

for referance, my altoptions line:
```

# nonaltoptions=quiet splash notsc elevator=cfq

```

(the elevator option is unrelated)

and run update-grub.


And I run several computers on smp, although only one X2, and they run 100% perfectly stable, I've had WAY WAY WAY less problems with my X2 on linux than I have on windows (where you basically need a hotfix which isn't released yet, and modify boot.ini aswell, and reinstall windows if you dont have your computertype set to acpi, as there is no way of changing that otherwise ;) ).

---

